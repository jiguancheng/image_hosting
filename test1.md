1．记录按照实验步骤操作所得到的 eg0101.s 的内容。

-   eg0101.s
    

```text
	.file	"eg0101.c"
	.intel_syntax noprefix
	.text
	.globl	add
	.type	add, @function
add:
.LFB0:
	.cfi_startproc
	lea	eax, [rdi+rsi]
	ret
	.cfi_endproc
.LFE0:
	.size	add, .-add
	.ident	"GCC: (Ubuntu 5.4.0-6ubuntu1~16.04.12) 5.4.0 20160609"
	.section	.note.GNU-stack,"",@progbits
```

---

2．记录按照实验步骤操作所得到的 eg0102.s 的内容。

-   eg0102.s
    

```text
	.file	"eg0102.c"
	.intel_syntax noprefix
	.text
	.globl	add
	.type	add, @function
add:
.LFB23:
	.cfi_startproc
	lea	eax, [rdi+rsi]
	ret
	.cfi_endproc
.LFE23:
	.size	add, .-add
	.section	.rodata.str1.1,"aMS",@progbits,1
.LC0:
	.string	"%d"
	.text
	.globl	main
	.type	main, @function
main:
.LFB24:
	.cfi_startproc
	sub	rsp, 8
	.cfi_def_cfa_offset 16
	mov	esi, 256
	mov	edi, 100
	call	add
	mov	edx, eax
	mov	esi, OFFSET FLAT:.LC0
	mov	edi, 1
	mov	eax, 0
	call	__printf_chk
	mov	eax, 0
	add	rsp, 8
	.cfi_def_cfa_offset 8
	ret
	.cfi_endproc
.LFE24:
	.size	main, .-main
	.ident	"GCC: (Ubuntu 5.4.0-6ubuntu1~16.04.12) 5.4.0 20160609"
	.section	.note.GNU-stack,"",@progbits
```

---

3．记录按照实验步骤操作 eg0101.o、 eg0101as.o、eg0101cc.o反汇编的结果。

-   objdump -d -M intel eg0101.o
    

```text

eg0101.o:     file format elf64-x86-64


Disassembly of section .text:

0000000000000000 <add>:
   0:	8d 04 37             	lea    eax,[rdi+rsi*1]
   3:	c3                   	ret 
```

-   objdump -d -M intel eg0101as.o
    

```text

eg0101as.o:     file format elf64-x86-64


Disassembly of section .text:

0000000000000000 <add>:
   0:	8d 04 37             	lea    eax,[rdi+rsi*1]
   3:	c3                   	ret    
```

-   objdump -d -M intel eg0101cc.o
    

```text

eg0101cc.o:     file format elf64-x86-64


Disassembly of section .text:

0000000000000000 <add>:
   0:	8d 04 37             	lea    eax,[rdi+rsi*1]
   3:	c3                   	ret    
```

---

4．记录按照实验步骤操作 eg0102.o 、eg0102\_1、eg0102as.o、eg0102cc.o、eg0102\_2反汇编的结果。

-   objdump -d -M intel eg0102.o
    

```text

eg0102.o:     file format elf64-x86-64


Disassembly of section .text:

0000000000000000 <add>:
   0:	8d 04 37             	lea    eax,[rdi+rsi*1]
   3:	c3                   	ret    

0000000000000004 <main>:
   4:	48 83 ec 08          	sub    rsp,0x8
   8:	be 00 01 00 00       	mov    esi,0x100
   d:	bf 64 00 00 00       	mov    edi,0x64
  12:	e8 00 00 00 00       	call   17 <main+0x13>
  17:	89 c2                	mov    edx,eax
  19:	be 00 00 00 00       	mov    esi,0x0
  1e:	bf 01 00 00 00       	mov    edi,0x1
  23:	b8 00 00 00 00       	mov    eax,0x0
  28:	e8 00 00 00 00       	call   2d <main+0x29>
  2d:	b8 00 00 00 00       	mov    eax,0x0
  32:	48 83 c4 08          	add    rsp,0x8
  36:	c3                   	ret    
```

-   objdump -d -M intel eg0102\_1
    

```text

eg0102_1:     file format elf64-x86-64


Disassembly of section .init:

00000000004003f0 <_init>:
  4003f0:	48 83 ec 08          	sub    rsp,0x8
  4003f4:	48 8b 05 fd 0b 20 00 	mov    rax,QWORD PTR [rip+0x200bfd]        # 600ff8 <_DYNAMIC+0x1d0>
  4003fb:	48 85 c0             	test   rax,rax
  4003fe:	74 05                	je     400405 <_init+0x15>
  400400:	e8 3b 00 00 00       	call   400440 <__printf_chk@plt+0x10>
  400405:	48 83 c4 08          	add    rsp,0x8
  400409:	c3                   	ret    

Disassembly of section .plt:

0000000000400410 <__libc_start_main@plt-0x10>:
  400410:	ff 35 f2 0b 20 00    	push   QWORD PTR [rip+0x200bf2]        # 601008 <_GLOBAL_OFFSET_TABLE_+0x8>
  400416:	ff 25 f4 0b 20 00    	jmp    QWORD PTR [rip+0x200bf4]        # 601010 <_GLOBAL_OFFSET_TABLE_+0x10>
  40041c:	0f 1f 40 00          	nop    DWORD PTR [rax+0x0]

0000000000400420 <__libc_start_main@plt>:
  400420:	ff 25 f2 0b 20 00    	jmp    QWORD PTR [rip+0x200bf2]        # 601018 <_GLOBAL_OFFSET_TABLE_+0x18>
  400426:	68 00 00 00 00       	push   0x0
  40042b:	e9 e0 ff ff ff       	jmp    400410 <_init+0x20>

0000000000400430 <__printf_chk@plt>:
  400430:	ff 25 ea 0b 20 00    	jmp    QWORD PTR [rip+0x200bea]        # 601020 <_GLOBAL_OFFSET_TABLE_+0x20>
  400436:	68 01 00 00 00       	push   0x1
  40043b:	e9 d0 ff ff ff       	jmp    400410 <_init+0x20>

Disassembly of section .plt.got:

0000000000400440 <.plt.got>:
  400440:	ff 25 b2 0b 20 00    	jmp    QWORD PTR [rip+0x200bb2]        # 600ff8 <_DYNAMIC+0x1d0>
  400446:	66 90                	xchg   ax,ax

Disassembly of section .text:

0000000000400450 <_start>:
  400450:	31 ed                	xor    ebp,ebp
  400452:	49 89 d1             	mov    r9,rdx
  400455:	5e                   	pop    rsi
  400456:	48 89 e2             	mov    rdx,rsp
  400459:	48 83 e4 f0          	and    rsp,0xfffffffffffffff0
  40045d:	50                   	push   rax
  40045e:	54                   	push   rsp
  40045f:	49 c7 c0 f0 05 40 00 	mov    r8,0x4005f0
  400466:	48 c7 c1 80 05 40 00 	mov    rcx,0x400580
  40046d:	48 c7 c7 4a 05 40 00 	mov    rdi,0x40054a
  400474:	e8 a7 ff ff ff       	call   400420 <__libc_start_main@plt>
  400479:	f4                   	hlt    
  40047a:	66 0f 1f 44 00 00    	nop    WORD PTR [rax+rax*1+0x0]

0000000000400480 <deregister_tm_clones>:
  400480:	b8 3f 10 60 00       	mov    eax,0x60103f
  400485:	55                   	push   rbp
  400486:	48 2d 38 10 60 00    	sub    rax,0x601038
  40048c:	48 83 f8 0e          	cmp    rax,0xe
  400490:	48 89 e5             	mov    rbp,rsp
  400493:	76 1b                	jbe    4004b0 <deregister_tm_clones+0x30>
  400495:	b8 00 00 00 00       	mov    eax,0x0
  40049a:	48 85 c0             	test   rax,rax
  40049d:	74 11                	je     4004b0 <deregister_tm_clones+0x30>
  40049f:	5d                   	pop    rbp
  4004a0:	bf 38 10 60 00       	mov    edi,0x601038
  4004a5:	ff e0                	jmp    rax
  4004a7:	66 0f 1f 84 00 00 00 	nop    WORD PTR [rax+rax*1+0x0]
  4004ae:	00 00 
  4004b0:	5d                   	pop    rbp
  4004b1:	c3                   	ret    
  4004b2:	0f 1f 40 00          	nop    DWORD PTR [rax+0x0]
  4004b6:	66 2e 0f 1f 84 00 00 	nop    WORD PTR cs:[rax+rax*1+0x0]
  4004bd:	00 00 00 

00000000004004c0 <register_tm_clones>:
  4004c0:	be 38 10 60 00       	mov    esi,0x601038
  4004c5:	55                   	push   rbp
  4004c6:	48 81 ee 38 10 60 00 	sub    rsi,0x601038
  4004cd:	48 c1 fe 03          	sar    rsi,0x3
  4004d1:	48 89 e5             	mov    rbp,rsp
  4004d4:	48 89 f0             	mov    rax,rsi
  4004d7:	48 c1 e8 3f          	shr    rax,0x3f
  4004db:	48 01 c6             	add    rsi,rax
  4004de:	48 d1 fe             	sar    rsi,1
  4004e1:	74 15                	je     4004f8 <register_tm_clones+0x38>
  4004e3:	b8 00 00 00 00       	mov    eax,0x0
  4004e8:	48 85 c0             	test   rax,rax
  4004eb:	74 0b                	je     4004f8 <register_tm_clones+0x38>
  4004ed:	5d                   	pop    rbp
  4004ee:	bf 38 10 60 00       	mov    edi,0x601038
  4004f3:	ff e0                	jmp    rax
  4004f5:	0f 1f 00             	nop    DWORD PTR [rax]
  4004f8:	5d                   	pop    rbp
  4004f9:	c3                   	ret    
  4004fa:	66 0f 1f 44 00 00    	nop    WORD PTR [rax+rax*1+0x0]

0000000000400500 <__do_global_dtors_aux>:
  400500:	80 3d 31 0b 20 00 00 	cmp    BYTE PTR [rip+0x200b31],0x0        # 601038 <__TMC_END__>
  400507:	75 11                	jne    40051a <__do_global_dtors_aux+0x1a>
  400509:	55                   	push   rbp
  40050a:	48 89 e5             	mov    rbp,rsp
  40050d:	e8 6e ff ff ff       	call   400480 <deregister_tm_clones>
  400512:	5d                   	pop    rbp
  400513:	c6 05 1e 0b 20 00 01 	mov    BYTE PTR [rip+0x200b1e],0x1        # 601038 <__TMC_END__>
  40051a:	f3 c3                	repz ret 
  40051c:	0f 1f 40 00          	nop    DWORD PTR [rax+0x0]

0000000000400520 <frame_dummy>:
  400520:	bf 20 0e 60 00       	mov    edi,0x600e20
  400525:	48 83 3f 00          	cmp    QWORD PTR [rdi],0x0
  400529:	75 05                	jne    400530 <frame_dummy+0x10>
  40052b:	eb 93                	jmp    4004c0 <register_tm_clones>
  40052d:	0f 1f 00             	nop    DWORD PTR [rax]
  400530:	b8 00 00 00 00       	mov    eax,0x0
  400535:	48 85 c0             	test   rax,rax
  400538:	74 f1                	je     40052b <frame_dummy+0xb>
  40053a:	55                   	push   rbp
  40053b:	48 89 e5             	mov    rbp,rsp
  40053e:	ff d0                	call   rax
  400540:	5d                   	pop    rbp
  400541:	e9 7a ff ff ff       	jmp    4004c0 <register_tm_clones>

0000000000400546 <add>:
  400546:	8d 04 37             	lea    eax,[rdi+rsi*1]
  400549:	c3                   	ret    

000000000040054a <main>:
  40054a:	48 83 ec 08          	sub    rsp,0x8
  40054e:	be 00 01 00 00       	mov    esi,0x100
  400553:	bf 64 00 00 00       	mov    edi,0x64
  400558:	e8 e9 ff ff ff       	call   400546 <add>
  40055d:	89 c2                	mov    edx,eax
  40055f:	be 04 06 40 00       	mov    esi,0x400604
  400564:	bf 01 00 00 00       	mov    edi,0x1
  400569:	b8 00 00 00 00       	mov    eax,0x0
  40056e:	e8 bd fe ff ff       	call   400430 <__printf_chk@plt>
  400573:	b8 00 00 00 00       	mov    eax,0x0
  400578:	48 83 c4 08          	add    rsp,0x8
  40057c:	c3                   	ret    
  40057d:	0f 1f 00             	nop    DWORD PTR [rax]

0000000000400580 <__libc_csu_init>:
  400580:	41 57                	push   r15
  400582:	41 56                	push   r14
  400584:	41 89 ff             	mov    r15d,edi
  400587:	41 55                	push   r13
  400589:	41 54                	push   r12
  40058b:	4c 8d 25 7e 08 20 00 	lea    r12,[rip+0x20087e]        # 600e10 <__frame_dummy_init_array_entry>
  400592:	55                   	push   rbp
  400593:	48 8d 2d 7e 08 20 00 	lea    rbp,[rip+0x20087e]        # 600e18 <__init_array_end>
  40059a:	53                   	push   rbx
  40059b:	49 89 f6             	mov    r14,rsi
  40059e:	49 89 d5             	mov    r13,rdx
  4005a1:	4c 29 e5             	sub    rbp,r12
  4005a4:	48 83 ec 08          	sub    rsp,0x8
  4005a8:	48 c1 fd 03          	sar    rbp,0x3
  4005ac:	e8 3f fe ff ff       	call   4003f0 <_init>
  4005b1:	48 85 ed             	test   rbp,rbp
  4005b4:	74 20                	je     4005d6 <__libc_csu_init+0x56>
  4005b6:	31 db                	xor    ebx,ebx
  4005b8:	0f 1f 84 00 00 00 00 	nop    DWORD PTR [rax+rax*1+0x0]
  4005bf:	00 
  4005c0:	4c 89 ea             	mov    rdx,r13
  4005c3:	4c 89 f6             	mov    rsi,r14
  4005c6:	44 89 ff             	mov    edi,r15d
  4005c9:	41 ff 14 dc          	call   QWORD PTR [r12+rbx*8]
  4005cd:	48 83 c3 01          	add    rbx,0x1
  4005d1:	48 39 eb             	cmp    rbx,rbp
  4005d4:	75 ea                	jne    4005c0 <__libc_csu_init+0x40>
  4005d6:	48 83 c4 08          	add    rsp,0x8
  4005da:	5b                   	pop    rbx
  4005db:	5d                   	pop    rbp
  4005dc:	41 5c                	pop    r12
  4005de:	41 5d                	pop    r13
  4005e0:	41 5e                	pop    r14
  4005e2:	41 5f                	pop    r15
  4005e4:	c3                   	ret    
  4005e5:	90                   	nop
  4005e6:	66 2e 0f 1f 84 00 00 	nop    WORD PTR cs:[rax+rax*1+0x0]
  4005ed:	00 00 00 

00000000004005f0 <__libc_csu_fini>:
  4005f0:	f3 c3                	repz ret 

Disassembly of section .fini:

00000000004005f4 <_fini>:
  4005f4:	48 83 ec 08          	sub    rsp,0x8
  4005f8:	48 83 c4 08          	add    rsp,0x8
  4005fc:	c3                   	ret    
```

-   objdump -d -M intel eg0102as.o
    

```text

eg0102as.o:     file format elf64-x86-64


Disassembly of section .text:

0000000000000000 <add>:
   0:	8d 04 37             	lea    eax,[rdi+rsi*1]
   3:	c3                   	ret    

0000000000000004 <main>:
   4:	48 83 ec 08          	sub    rsp,0x8
   8:	be 00 01 00 00       	mov    esi,0x100
   d:	bf 64 00 00 00       	mov    edi,0x64
  12:	e8 00 00 00 00       	call   17 <main+0x13>
  17:	89 c2                	mov    edx,eax
  19:	be 00 00 00 00       	mov    esi,0x0
  1e:	bf 01 00 00 00       	mov    edi,0x1
  23:	b8 00 00 00 00       	mov    eax,0x0
  28:	e8 00 00 00 00       	call   2d <main+0x29>
  2d:	b8 00 00 00 00       	mov    eax,0x0
  32:	48 83 c4 08          	add    rsp,0x8
  36:	c3                   	ret    
```

-   objdump -d -M intel eg0102cc.o
    

```text

eg0102cc.o:     file format elf64-x86-64


Disassembly of section .text:

0000000000000000 <add>:
   0:	8d 04 37             	lea    eax,[rdi+rsi*1]
   3:	c3                   	ret    

0000000000000004 <main>:
   4:	48 83 ec 08          	sub    rsp,0x8
   8:	be 00 01 00 00       	mov    esi,0x100
   d:	bf 64 00 00 00       	mov    edi,0x64
  12:	e8 00 00 00 00       	call   17 <main+0x13>
  17:	89 c2                	mov    edx,eax
  19:	be 00 00 00 00       	mov    esi,0x0
  1e:	bf 01 00 00 00       	mov    edi,0x1
  23:	b8 00 00 00 00       	mov    eax,0x0
  28:	e8 00 00 00 00       	call   2d <main+0x29>
  2d:	b8 00 00 00 00       	mov    eax,0x0
  32:	48 83 c4 08          	add    rsp,0x8
  36:	c3                   	ret    
```

-   objdump -d -M intel eg0102\_2
    

```text

eg0102_2:     file format elf64-x86-64


Disassembly of section .init:

00000000004003f0 <_init>:
  4003f0:	48 83 ec 08          	sub    rsp,0x8
  4003f4:	48 8b 05 fd 0b 20 00 	mov    rax,QWORD PTR [rip+0x200bfd]        # 600ff8 <_DYNAMIC+0x1d0>
  4003fb:	48 85 c0             	test   rax,rax
  4003fe:	74 05                	je     400405 <_init+0x15>
  400400:	e8 3b 00 00 00       	call   400440 <__printf_chk@plt+0x10>
  400405:	48 83 c4 08          	add    rsp,0x8
  400409:	c3                   	ret    

Disassembly of section .plt:

0000000000400410 <__libc_start_main@plt-0x10>:
  400410:	ff 35 f2 0b 20 00    	push   QWORD PTR [rip+0x200bf2]        # 601008 <_GLOBAL_OFFSET_TABLE_+0x8>
  400416:	ff 25 f4 0b 20 00    	jmp    QWORD PTR [rip+0x200bf4]        # 601010 <_GLOBAL_OFFSET_TABLE_+0x10>
  40041c:	0f 1f 40 00          	nop    DWORD PTR [rax+0x0]

0000000000400420 <__libc_start_main@plt>:
  400420:	ff 25 f2 0b 20 00    	jmp    QWORD PTR [rip+0x200bf2]        # 601018 <_GLOBAL_OFFSET_TABLE_+0x18>
  400426:	68 00 00 00 00       	push   0x0
  40042b:	e9 e0 ff ff ff       	jmp    400410 <_init+0x20>

0000000000400430 <__printf_chk@plt>:
  400430:	ff 25 ea 0b 20 00    	jmp    QWORD PTR [rip+0x200bea]        # 601020 <_GLOBAL_OFFSET_TABLE_+0x20>
  400436:	68 01 00 00 00       	push   0x1
  40043b:	e9 d0 ff ff ff       	jmp    400410 <_init+0x20>

Disassembly of section .plt.got:

0000000000400440 <.plt.got>:
  400440:	ff 25 b2 0b 20 00    	jmp    QWORD PTR [rip+0x200bb2]        # 600ff8 <_DYNAMIC+0x1d0>
  400446:	66 90                	xchg   ax,ax

Disassembly of section .text:

0000000000400450 <_start>:
  400450:	31 ed                	xor    ebp,ebp
  400452:	49 89 d1             	mov    r9,rdx
  400455:	5e                   	pop    rsi
  400456:	48 89 e2             	mov    rdx,rsp
  400459:	48 83 e4 f0          	and    rsp,0xfffffffffffffff0
  40045d:	50                   	push   rax
  40045e:	54                   	push   rsp
  40045f:	49 c7 c0 f0 05 40 00 	mov    r8,0x4005f0
  400466:	48 c7 c1 80 05 40 00 	mov    rcx,0x400580
  40046d:	48 c7 c7 4a 05 40 00 	mov    rdi,0x40054a
  400474:	e8 a7 ff ff ff       	call   400420 <__libc_start_main@plt>
  400479:	f4                   	hlt    
  40047a:	66 0f 1f 44 00 00    	nop    WORD PTR [rax+rax*1+0x0]

0000000000400480 <deregister_tm_clones>:
  400480:	b8 3f 10 60 00       	mov    eax,0x60103f
  400485:	55                   	push   rbp
  400486:	48 2d 38 10 60 00    	sub    rax,0x601038
  40048c:	48 83 f8 0e          	cmp    rax,0xe
  400490:	48 89 e5             	mov    rbp,rsp
  400493:	76 1b                	jbe    4004b0 <deregister_tm_clones+0x30>
  400495:	b8 00 00 00 00       	mov    eax,0x0
  40049a:	48 85 c0             	test   rax,rax
  40049d:	74 11                	je     4004b0 <deregister_tm_clones+0x30>
  40049f:	5d                   	pop    rbp
  4004a0:	bf 38 10 60 00       	mov    edi,0x601038
  4004a5:	ff e0                	jmp    rax
  4004a7:	66 0f 1f 84 00 00 00 	nop    WORD PTR [rax+rax*1+0x0]
  4004ae:	00 00 
  4004b0:	5d                   	pop    rbp
  4004b1:	c3                   	ret    
  4004b2:	0f 1f 40 00          	nop    DWORD PTR [rax+0x0]
  4004b6:	66 2e 0f 1f 84 00 00 	nop    WORD PTR cs:[rax+rax*1+0x0]
  4004bd:	00 00 00 

00000000004004c0 <register_tm_clones>:
  4004c0:	be 38 10 60 00       	mov    esi,0x601038
  4004c5:	55                   	push   rbp
  4004c6:	48 81 ee 38 10 60 00 	sub    rsi,0x601038
  4004cd:	48 c1 fe 03          	sar    rsi,0x3
  4004d1:	48 89 e5             	mov    rbp,rsp
  4004d4:	48 89 f0             	mov    rax,rsi
  4004d7:	48 c1 e8 3f          	shr    rax,0x3f
  4004db:	48 01 c6             	add    rsi,rax
  4004de:	48 d1 fe             	sar    rsi,1
  4004e1:	74 15                	je     4004f8 <register_tm_clones+0x38>
  4004e3:	b8 00 00 00 00       	mov    eax,0x0
  4004e8:	48 85 c0             	test   rax,rax
  4004eb:	74 0b                	je     4004f8 <register_tm_clones+0x38>
  4004ed:	5d                   	pop    rbp
  4004ee:	bf 38 10 60 00       	mov    edi,0x601038
  4004f3:	ff e0                	jmp    rax
  4004f5:	0f 1f 00             	nop    DWORD PTR [rax]
  4004f8:	5d                   	pop    rbp
  4004f9:	c3                   	ret    
  4004fa:	66 0f 1f 44 00 00    	nop    WORD PTR [rax+rax*1+0x0]

0000000000400500 <__do_global_dtors_aux>:
  400500:	80 3d 31 0b 20 00 00 	cmp    BYTE PTR [rip+0x200b31],0x0        # 601038 <__TMC_END__>
  400507:	75 11                	jne    40051a <__do_global_dtors_aux+0x1a>
  400509:	55                   	push   rbp
  40050a:	48 89 e5             	mov    rbp,rsp
  40050d:	e8 6e ff ff ff       	call   400480 <deregister_tm_clones>
  400512:	5d                   	pop    rbp
  400513:	c6 05 1e 0b 20 00 01 	mov    BYTE PTR [rip+0x200b1e],0x1        # 601038 <__TMC_END__>
  40051a:	f3 c3                	repz ret 
  40051c:	0f 1f 40 00          	nop    DWORD PTR [rax+0x0]

0000000000400520 <frame_dummy>:
  400520:	bf 20 0e 60 00       	mov    edi,0x600e20
  400525:	48 83 3f 00          	cmp    QWORD PTR [rdi],0x0
  400529:	75 05                	jne    400530 <frame_dummy+0x10>
  40052b:	eb 93                	jmp    4004c0 <register_tm_clones>
  40052d:	0f 1f 00             	nop    DWORD PTR [rax]
  400530:	b8 00 00 00 00       	mov    eax,0x0
  400535:	48 85 c0             	test   rax,rax
  400538:	74 f1                	je     40052b <frame_dummy+0xb>
  40053a:	55                   	push   rbp
  40053b:	48 89 e5             	mov    rbp,rsp
  40053e:	ff d0                	call   rax
  400540:	5d                   	pop    rbp
  400541:	e9 7a ff ff ff       	jmp    4004c0 <register_tm_clones>

0000000000400546 <add>:
  400546:	8d 04 37             	lea    eax,[rdi+rsi*1]
  400549:	c3                   	ret    

000000000040054a <main>:
  40054a:	48 83 ec 08          	sub    rsp,0x8
  40054e:	be 00 01 00 00       	mov    esi,0x100
  400553:	bf 64 00 00 00       	mov    edi,0x64
  400558:	e8 e9 ff ff ff       	call   400546 <add>
  40055d:	89 c2                	mov    edx,eax
  40055f:	be 04 06 40 00       	mov    esi,0x400604
  400564:	bf 01 00 00 00       	mov    edi,0x1
  400569:	b8 00 00 00 00       	mov    eax,0x0
  40056e:	e8 bd fe ff ff       	call   400430 <__printf_chk@plt>
  400573:	b8 00 00 00 00       	mov    eax,0x0
  400578:	48 83 c4 08          	add    rsp,0x8
  40057c:	c3                   	ret    
  40057d:	0f 1f 00             	nop    DWORD PTR [rax]

0000000000400580 <__libc_csu_init>:
  400580:	41 57                	push   r15
  400582:	41 56                	push   r14
  400584:	41 89 ff             	mov    r15d,edi
  400587:	41 55                	push   r13
  400589:	41 54                	push   r12
  40058b:	4c 8d 25 7e 08 20 00 	lea    r12,[rip+0x20087e]        # 600e10 <__frame_dummy_init_array_entry>
  400592:	55                   	push   rbp
  400593:	48 8d 2d 7e 08 20 00 	lea    rbp,[rip+0x20087e]        # 600e18 <__init_array_end>
  40059a:	53                   	push   rbx
  40059b:	49 89 f6             	mov    r14,rsi
  40059e:	49 89 d5             	mov    r13,rdx
  4005a1:	4c 29 e5             	sub    rbp,r12
  4005a4:	48 83 ec 08          	sub    rsp,0x8
  4005a8:	48 c1 fd 03          	sar    rbp,0x3
  4005ac:	e8 3f fe ff ff       	call   4003f0 <_init>
  4005b1:	48 85 ed             	test   rbp,rbp
  4005b4:	74 20                	je     4005d6 <__libc_csu_init+0x56>
  4005b6:	31 db                	xor    ebx,ebx
  4005b8:	0f 1f 84 00 00 00 00 	nop    DWORD PTR [rax+rax*1+0x0]
  4005bf:	00 
  4005c0:	4c 89 ea             	mov    rdx,r13
  4005c3:	4c 89 f6             	mov    rsi,r14
  4005c6:	44 89 ff             	mov    edi,r15d
  4005c9:	41 ff 14 dc          	call   QWORD PTR [r12+rbx*8]
  4005cd:	48 83 c3 01          	add    rbx,0x1
  4005d1:	48 39 eb             	cmp    rbx,rbp
  4005d4:	75 ea                	jne    4005c0 <__libc_csu_init+0x40>
  4005d6:	48 83 c4 08          	add    rsp,0x8
  4005da:	5b                   	pop    rbx
  4005db:	5d                   	pop    rbp
  4005dc:	41 5c                	pop    r12
  4005de:	41 5d                	pop    r13
  4005e0:	41 5e                	pop    r14
  4005e2:	41 5f                	pop    r15
  4005e4:	c3                   	ret    
  4005e5:	90                   	nop
  4005e6:	66 2e 0f 1f 84 00 00 	nop    WORD PTR cs:[rax+rax*1+0x0]
  4005ed:	00 00 00 

00000000004005f0 <__libc_csu_fini>:
  4005f0:	f3 c3                	repz ret 

Disassembly of section .fini:

00000000004005f4 <_fini>:
  4005f4:	48 83 ec 08          	sub    rsp,0x8
  4005f8:	48 83 c4 08          	add    rsp,0x8
  4005fc:	c3                   	ret    
```

---

5．编译时参数“-Og ”改成 “-O1、-O2、或-O3 ”所得到的汇编语言文件是否一样？你认为是什么原因？

得到的汇编语言文件不完全一样。

`-Og`参数优先保证调试体验；`-O1`、`-O2`、`-O3`参数是不同级别的优化，`-O1`是默认优化，`-O3`优化级别最高。

---

6．目标文件 eg0102.o 和可执行文件 eg0102 反汇编结果是否一样？你认为是什么原因？

反汇编结果不一样。

可执行文件在目标文件的基础上进行了链接，将使用到的其它文件合并到了一起。

---

7．根据 eg0101.s 和 eg0102.s 的共同部分，总结 GAS 汇编语言程序框架。

这个跳过吧。

---

8．写出汇编语言源程序 exp0104.s的源程序，汇编连接方法及运行结果截图。

-   exp0104.s
    

```text
    .intel_syntax noprefix
    .data
     msg:  .asciz "Hello, Assembly!\n"
    .text
    .globl main
    main:
    lea rax,  msg[rip]
    call dispmsg
    mov eax, 0
    ret
```

-   汇编
    

```bash
gcc -Wa,-alm -o exp0104.o exp0104.s /headless/Desktop/ZZUassembly/ZZUGAS/lib/io_linux64.a
```

-   链接
    

```bash
gcc -o exp0104 exp0104.s /headless/Desktop/ZZUassembly/ZZUGAS/lib/io_linux64.a
```

-   运行
    

```bash
./exp0104
```

-   运行结果截图
    
    ![pasted_image_ea3f74c8-7367-4c59-a5eb-67c21e259650.png](http://10.67.4.14/cguserImages?_stuimg=40987ac900bb14c0b2ab6c52ae5dd2bc.jpeg)

---

9．总结汇编语言程序开发过程的经验体会，写出自己遇到的或感到困惑的问题等。

使用汇编语言进行开发过于繁琐，过于麻烦。

困惑：关键字过多，且过于简短；遇到不认识的关键字也很难从名字推断用途，很麻烦；需要记很多东西。
