<summary><b>Task 6:</b> Completed code along with a brief demonstration video of the application</summary>

## Complete setup
![Circuit Connection](https://github.com/nishit0072e/vsd-mini/blob/main/images/1741276396181.jpg)

## Working C Program

```c
// 4-Bit Linear Feedback Shift Register C code tailored for CH32V003 Microcontroller

#include <ch32v00x.h>

#define LFSR_SEED       0x9    // Initial seed (must be nonzero)
#define DELAY_TIME_MS   200    // Delay in milliseconds 

void My_GPIO_Init(void);
void My_Delay_Ms(uint32_t n);  

int main(void) {
    uint8_t lfsr = LFSR_SEED; // Initialize with a seed
    uint8_t bit;              // Feedback bit

    SystemInit();     // Initialize system to 24 MHz
    My_GPIO_Init();   // Configure GPIOs

    while (1) {
        // Output LFSR bits to PD1 - PD4
        GPIO_WriteBit(GPIOC, GPIO_Pin_3, (lfsr & 0x1) ? Bit_SET : Bit_RESET);
        GPIO_WriteBit(GPIOC, GPIO_Pin_4, (lfsr & 0x2) ? Bit_SET : Bit_RESET);
        GPIO_WriteBit(GPIOC, GPIO_Pin_5, (lfsr & 0x4) ? Bit_SET : Bit_RESET);
        GPIO_WriteBit(GPIOC, GPIO_Pin_6, (lfsr & 0x8) ? Bit_SET : Bit_RESET);

        // Compute feedback bit (XOR MSB and second MSB)
        bit = ((lfsr >> 3) ^ (lfsr >> 2)) & 1;

        // Shift and insert feedback bit
        lfsr = ((lfsr << 1) | bit) & 0xF; 

        My_Delay_Ms(DELAY_TIME_MS); // Use renamed delay function
    }
}

void My_GPIO_Init(void) {
    GPIO_InitTypeDef GPIO_InitStructure;

    RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOC, ENABLE);  // Enable PC clock

    GPIO_InitStructure.GPIO_Pin = GPIO_Pin_3 | GPIO_Pin_4 | GPIO_Pin_5 | GPIO_Pin_6;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP;  
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_10MHz;
    GPIO_Init(GPIOC, &GPIO_InitStructure);  
}

void My_Delay_Ms(uint32_t n) {
    // Calibrated for 24 MHz clock
    // 24,000,000 cycles/sec ÷ 1000 = 24,000 cycles/ms
    volatile uint32_t cycles_per_ms = 24000 / 3;  // 8000 cycles per ms
    volatile uint32_t i = n * cycles_per_ms;
    
    while (i--) {
        __NOP();  // 1 cycle
    }
}
```

### **LFSR Video:**
[Click Here](https://drive.google.com/file/d/12UFlZ1OrSupuZroSccUdJK6XQvvZt9e7/view?usp=sharing) to see the functioning of 4-Bit LFSR on VSDSquadron Mini Board
