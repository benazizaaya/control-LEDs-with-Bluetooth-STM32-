################################################################################
# Automatically-generated file. Do not edit!
# Toolchain: GNU Tools for STM32 (11.3.rel1)
################################################################################

-include ../makefile.init

RM := del /F /Q

# All of the sources participating in the build are defined here
-include sources.mk
-include Drivers/STM32F4xx_HAL_Driver/Src/subdir.mk
-include Core/Startup/subdir.mk
-include Core/Src/subdir.mk
-include objects.mk

ifneq ($(MAKECMDGOALS),clean)
ifneq ($(strip $(S_DEPS)),)
-include $(S_DEPS)
endif
ifneq ($(strip $(S_UPPER_DEPS)),)
-include $(S_UPPER_DEPS)
endif
ifneq ($(strip $(C_DEPS)),)
-include $(C_DEPS)
endif
endif

-include ../makefile.defs

OPTIONAL_TOOL_DEPS := \
$(wildcard ../makefile.defs) \
$(wildcard ../makefile.init) \
$(wildcard ../makefile.targets)

BUILD_ARTIFACT_NAME := led_blink_with_bt
BUILD_ARTIFACT_EXTENSION := elf
BUILD_ARTIFACT_PREFIX :=
BUILD_ARTIFACT := $(BUILD_ARTIFACT_PREFIX)$(BUILD_ARTIFACT_NAME)$(if $(BUILD_ARTIFACT_EXTENSION),.$(BUILD_ARTIFACT_EXTENSION),)

# Add inputs and outputs from these tool invocations to the build variables
EXECUTABLES += \
$(BUILD_ARTIFACT) \

MAP_FILES += \
$(BUILD_ARTIFACT_NAME).map \

SIZE_OUTPUT += \
default.size.stdout \

OBJDUMP_LIST += \
$(BUILD_ARTIFACT_NAME).list \

BIN_FILE := $(BUILD_ARTIFACT_NAME).bin

# All Target
all: main-build

# Main-build Target
main-build: $(BUILD_ARTIFACT) secondary-outputs $(BIN_FILE)

# Tool invocations
$(BUILD_ARTIFACT): $(OBJS) $(USER_OBJS) $(LINKER_SCRIPT) makefile objects.list $(OPTIONAL_TOOL_DEPS)
	arm-none-eabi-gcc -o $(BUILD_ARTIFACT) @objects.list $(USER_OBJS) $(LIBS) -mcpu=cortex-m4 -T$(LINKER_SCRIPT) --specs=nosys.specs -Wl,-Map=$(BUILD_ARTIFACT_NAME).map -Wl,--gc-sections -static --specs=nano.specs -mfpu=fpv4-sp-d16 -mfloat-abi=hard -mthumb -Wl,--start-group -lc -lm -Wl,--end-group
	@echo 'Finished building target: $@'
	@echo ' '

$(BIN_FILE): $(BUILD_ARTIFACT)
	arm-none-eabi-objcopy -O binary $(BUILD_ARTIFACT) $(BIN_FILE)
	@echo 'Generated binary file: $@'
	@echo ' '

default.size.stdout: $(EXECUTABLES) makefile objects.list $(OPTIONAL_TOOL_DEPS)
	arm-none-eabi-size  $(EXECUTABLES)
	@echo 'Finished building: $@'
	@echo ' '

$(BUILD_ARTIFACT_NAME).list: $(EXECUTABLES) makefile objects.list $(OPTIONAL_TOOL_DEPS)
	arm-none-eabi-objdump -h -S $(EXECUTABLES) > $(BUILD_ARTIFACT_NAME).list
	@echo 'Finished building: $@'
	@echo ' '

# Other Targets
clean:
	-$(RM) default.size.stdout $(BUILD_ARTIFACT) $(BUILD_ARTIFACT_NAME).list $(BUILD_ARTIFACT_NAME).map $(BIN_FILE) $(OBJ_FILES) $(DEP_FILES)
	-@echo ' '

secondary-outputs: $(SIZE_OUTPUT) $(OBJDUMP_LIST)

.PHONY: all clean dependents main-build
