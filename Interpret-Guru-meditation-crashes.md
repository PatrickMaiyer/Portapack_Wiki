Sometimes your program is having a bad day, and it's simply crashing the whole machine. We added an error screen for developers who don't have a 
[Black Magic Probe](https://hackrf.readthedocs.io/en/latest/LPC43XX_Debugging.html)
sitting around and ready to use. You should still be able to narrow down the location where the error is coming from.

![screen](https://user-images.githubusercontent.com/13151053/224955725-21e95915-3b9d-4e2e-9280-2b1d6a111376.jpg)

## Information On Screen

* The first line already contains the first very important piece.
  * M0: the crash occured in the application firmware
  * M4: the crash occured in the baseband firmware
* The Hint can be
  * Hard Fault: indicates an invalid operation. (eg. invalid memory access)
  * MemManage: indicates a memory fault
  * BusFault: indicates a bus fault
  * UsageFault: indicates a usage fault
  * some other text like 'NoImg' or 'BBRunning' (see usages of 'chDbgPanic(const char *)')
* Registers (only visible in case of a Hard Fault)
  * r0-r3 & r12: The values of the registers at the time of the fault.
  * lr: The link register contains the return address of the calling method. Use this value only if the process counter is unusable.
  * pc: The process counter is the location of the current instruction. Use this value in the next step.

## Determining the location in C/C++ source

* Run the following command to get the assembly at the location.
  * Replace 0xd440 with your pc/lr value
  * use firmware/application/application.elf only for M0 errors. Use the currently loaded baseband image for M4 errors. (eg. firmware/baseband/baseband_adsbrx.elf)
```console
dev@ubuntu:~$ cd build
dev@ubuntu:~$ arm-none-eabi-gdb --q -ex="x/3i 0xd440" --batch firmware/application/application.elf
   0xd440 <luaD_protectedparser>:       push    {r4, r5, r6, lr}
   0xd442 <luaD_protectedparser+2>:     movs    r5, #0
   0xd444 <luaD_protectedparser+4>:     sub     sp, #32
```

*  Or run the following command to disassemble the whole image.
```console
dev@ubuntu:~$ cd build
dev@ubuntu:~$ arm-none-eabi-objdump --source firmware/application/application.elf > firmware/application/application.objdump
```
  * then inspect the file firmware/application/application.objdump to get the full picture.
```cpp
[...]
int luaD_protectedparser (lua_State *L, ZIO *z, const char *name) {
    d440:	b570      	push	{r4, r5, r6, lr}
  struct SParser p;
  int status;
  p.z = z; p.name = name;
  luaZ_initbuffer(L, &p.buff);
    d442:	2500      	movs	r5, #0
int luaD_protectedparser (lua_State *L, ZIO *z, const char *name) {
    d444:	b088      	sub	sp, #32
  status = luaD_pcall(L, f_parser, &p, savestack(L, L->top), L->errfunc);
    d446:	6883      	ldr	r3, [r0, #8]
[...]
```
## M0 Stack Dump

After a crash, pressing the DFU button will display the M0 core's stack contents, which can be paged up & down.  All stack words are shown beginning with the first stack word that has been used since powering up the PortaPack (which may not correspond with the current stack pointer).  If the LR value is known, stack words containing the value matching the LR where the fault occurred will be highlighted in yellow.  Stack words containing values that might possibly be addresses in the code region are highlighted in white.

## More useful Information

* [How to debug a HardFault on an ARM Cortex-M on interrupt.memfault.com](https://interrupt.memfault.com/blog/cortex-m-hardfault-debug)
* You can read the related PR with instructions [here](https://github.com/eried/portapack-mayhem/pull/830)
