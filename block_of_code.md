# Block of Code

*Some of code sample written by me. This was a code written to  develop a complete assembly program based on the given auxiliary board hardware. The program should be able to control the LEDs on the board to switch them off or on. It will perform bit-wise operations and Interface with the LEDs on the auxiliary board through GPIOs from the raspberry Pi.*


# Assembly 

.data
	gpio_base:    .word	0
	
.text
.global main

main:
	@ Assume that the GPIO base address
	@ has already been loaded
	
	
	ldr r3, =gpio_base
	ldr r5,[r3]
	bic r5,r5,#0b111<<6       //GPIO2
	orr r5,r5,#0b001<<6
	str r5,[r3]
	
	ldr r5,[r3]
	bic r5,r5,#0b111<<9       //GPIO3
	orr r5,r5,#0b001<<9
	str r5,[r3]
	
	ldr r5,[r3]
	bic r5,r5,#0b111<<12       //GPIO4
	orr r5,r5,#0b001<<12
	str r5,[r3]
	
	ldr r5,[r3]
	bic r5,r5,#0b111<<15       //GPIO5
	orr r5,r5,#0b001<<15
	str r5,[r3]
	
	add r5,r3,#28
	mov r4,#0b101
	mov r4,r4,lsl#2            //Set GPIO2 and GPIO4 to 1
	str r4,[r5]

    add r5,r3,#40
	mov r4,#0b101             //Clear GPIO3 and GPIO5 to 0
	mov r4,r4,lsl#3
	str r4,[r5]
	



        @ exit syscall
        mov r7, #1
        swi 0


[Home Page](./README.md)
