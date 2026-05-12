# Операционные системы
# 1 лабораторная
### Реализации фибоначи на с++
<img width="463" height="262" alt="1" src="https://github.com/user-attachments/assets/d513e205-c7c3-4b23-91f4-9b095d1dafc9" /> <br>
<img width="396" height="138" alt="2" src="https://github.com/user-attachments/assets/b1667b4c-2660-4bc0-bf95-b5d0aeade5c5" /><br>
<img width="368" height="287" alt="3" src="https://github.com/user-attachments/assets/ce2fe7e6-e444-4646-b06d-49b5041564b2" /><br>

### проверка на работу кода 
<img width="680" height="193" alt="4" src="https://github.com/user-attachments/assets/fd2722d0-c003-4b57-91ea-5a53cad2dd1f" /><br>

### компилация в код для ассемблера
<img width="698" height="153" alt="5 0" src="https://github.com/user-attachments/assets/b13600bb-9acf-4f9a-a592-fd725df53b71" /><br>

### без оптимизации
<img width="915" height="765" alt="5" src="https://github.com/user-attachments/assets/ab8518fd-dac5-4cfc-b0bf-ecdf0cd51277" />

### c -O3 оптимизацией (вставка кодом, тк в один скрин не помещался)
```asm
	.file	"factorial.cpp"
	.text
	.p2align 4,,15
	.globl	_Z9factoriali
	.def	_Z9factoriali;	.scl	2;	.type	32;	.endef
	.seh_proc	_Z9factoriali
_Z9factoriali:
.LFB0:
	subq	$56, %rsp
	.seh_stackalloc	56
	movaps	%xmm6, (%rsp)
	.seh_savexmm	%xmm6, 0
	movaps	%xmm7, 16(%rsp)
	.seh_savexmm	%xmm7, 16
	movaps	%xmm8, 32(%rsp)
	.seh_savexmm	%xmm8, 32
	.seh_endprologue
	testl	%ecx, %ecx
	jle	.L7
	leal	-1(%rcx), %eax
	cmpl	$5, %eax
	jbe	.L8
	movl	%ecx, %edx
	xorl	%eax, %eax
	pxor	%xmm7, %xmm7
	movdqa	.LC0(%rip), %xmm3
	movdqa	.LC1(%rip), %xmm4
	shrl	$2, %edx
	movdqa	.LC2(%rip), %xmm8
	.p2align 4,,10
.L5:
	movdqa	%xmm7, %xmm0
	movdqa	%xmm3, %xmm5
	movdqa	%xmm3, %xmm6
	pcmpgtd	%xmm3, %xmm0
	addl	$1, %eax
	paddd	%xmm8, %xmm3
	cmpl	%edx, %eax
	punpckldq	%xmm0, %xmm5
	punpckhdq	%xmm0, %xmm6
	movdqa	%xmm5, %xmm1
	movdqa	%xmm6, %xmm0
	psrlq	$32, %xmm1
	movdqa	%xmm5, %xmm2
	psrlq	$32, %xmm0
	pmuludq	%xmm5, %xmm0
	pmuludq	%xmm6, %xmm1
	pmuludq	%xmm6, %xmm2
	paddq	%xmm0, %xmm1
	psllq	$32, %xmm1
	paddq	%xmm2, %xmm1
	movdqa	%xmm4, %xmm2
	movdqa	%xmm1, %xmm0
	psrlq	$32, %xmm2
	movdqa	%xmm1, %xmm5
	psrlq	$32, %xmm0
	pmuludq	%xmm4, %xmm0
	pmuludq	%xmm2, %xmm1
	pmuludq	%xmm4, %xmm5
	paddq	%xmm1, %xmm0
	psllq	$32, %xmm0
	movdqa	%xmm5, %xmm4
	paddq	%xmm0, %xmm4
	jne	.L5
	movdqa	%xmm4, %xmm3
	movdqa	%xmm4, %xmm0
	movdqa	%xmm4, %xmm1
	psrldq	$8, %xmm3
	movl	%ecx, %r8d
	movdqa	%xmm3, %xmm2
	psrlq	$32, %xmm0
	andl	$-4, %r8d
	psrlq	$32, %xmm2
	leal	1(%r8), %edx
	cmpl	%r8d, %ecx
	pmuludq	%xmm3, %xmm0
	pmuludq	%xmm2, %xmm4
	pmuludq	%xmm3, %xmm1
	paddq	%xmm4, %xmm0
	psllq	$32, %xmm0
	paddq	%xmm1, %xmm0
	movq	%xmm0, %rax
	je	.L1
.L3:
	movslq	%edx, %r8
	imulq	%r8, %rax
	leal	1(%rdx), %r8d
	cmpl	%r8d, %ecx
	jl	.L1
	movslq	%r8d, %r8
	imulq	%r8, %rax
	leal	2(%rdx), %r8d
	cmpl	%r8d, %ecx
	jl	.L1
	movslq	%r8d, %r8
	imulq	%r8, %rax
	leal	3(%rdx), %r8d
	cmpl	%r8d, %ecx
	jl	.L1
	movslq	%r8d, %r8
	imulq	%r8, %rax
	leal	4(%rdx), %r8d
	cmpl	%r8d, %ecx
	jl	.L1
	movslq	%r8d, %r8
	addl	$5, %edx
	imulq	%r8, %rax
	cmpl	%edx, %ecx
	jl	.L1
	movslq	%edx, %rdx
	imulq	%rdx, %rax
.L1:
	movaps	(%rsp), %xmm6
	movaps	16(%rsp), %xmm7
	movaps	32(%rsp), %xmm8
	addq	$56, %rsp
	ret
	.p2align 4,,10
.L7:
	movl	$1, %eax
	jmp	.L1
.L8:
	movl	$1, %edx
	movl	$1, %eax
	jmp	.L3
	.seh_endproc
	.section .rdata,"dr"
	.align 16
.LC0:
	.long	1
	.long	2
	.long	3
	.long	4
	.align 16
.LC1:
	.quad	1
	.quad	1
	.align 16
.LC2:
	.long	4
	.long	4
	.long	4
	.long	4
	.ident	"GCC: (x86_64-posix-seh-rev0, Built by MinGW-W64 project) 8.1.0"
```
### создаем Makefile
<img width="588" height="423" alt="6" src="https://github.com/user-attachments/assets/7c69e2db-e396-4d65-8cb9-d8d28db2bba3" />

### запуск Makefile
<img width="541" height="170" alt="7" src="https://github.com/user-attachments/assets/6ed36a44-0145-40ed-a4c6-f0e09c0648b5" />

### Чтобы усовершенствовать программу, добавим два параллельных потока вычислений. Каждый поток вычисляет факториал своего числа (15! и 20!). Основной поток запускает их параллельно, выполняет свою работу, а затем синхронизируется с ними через join(), ожидая завершения вычислений. Результаты передаются через общие переменные res1 и res2, доступ к которым синхронизируется автоматически благодаря вызову join()
<img width="597" height="717" alt="8" src="https://github.com/user-attachments/assets/d5e89558-ffce-48ea-923c-f2f31f54bffb" />

### В Makefile добавлен флаг -pthread для поддержки многопоточности
<img width="592" height="515" alt="9" src="https://github.com/user-attachments/assets/6e64c02d-714c-4e7d-b9bf-c5bd6479d1b3" />

### Запускаем Makefile (второй запуск без -pthread выдает ошибку)
<img width="412" height="208" alt="10" src="https://github.com/user-attachments/assets/c05321e1-e4ef-4c6b-9e6e-16d302c5cc46" />


