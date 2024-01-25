# Assignment: Exploring Real-World Code Examples
## Introduction
In our everyday lives, we interact with a myriad of software applications, often without realizing the complex code that powers them. From the moment we silence our morning alarm, to checking the weather forecast, or even making an online purchase, software is an integral part of our daily routine. As we embark on our journey to learn coding, it's essential to understand how these applications are built and function. This assignment, designed for beginners, leverages our newly acquired skills in using GitHub and other online repositories. It's an opportunity to explore and connect with the real-world applications of code.

## Objective
Your task is to delve into the world of coding by finding real-life examples of code that power the software applications you use daily. This exercise will help you understand how theoretical coding concepts are applied in practical, real-world scenarios.

## Assignment Details
Research and Exploration: Using online repositories like GitHub, search for code examples that align with the everyday software applications described in the provided prose blurbs.

Link and Line Numbers: For each example, provide the link to the code repository and specify the exact line numbers where the relevant code is located. This will help you practice navigating through code repositories and understanding code structure.

Documentation: Along with each link, write a brief description of what the code does and how it relates to the functionality of the application in the real world.

## Prose Blurbs for Exploration
- Code that specifies when an alarm clock should start making audible sounds.
https://github.com/yuriykulikov/AlarmClock <- Link to repository
https://github.com/yuriykulikov/AlarmClock/blob/develop/app/src/androidTest/java/com/better/alarm/test/InfoFragmentTest.kt <- Link to specific location
@Test
  fun prealarmOn3Days() {
    val now = Calendar.getInstance().timeInMillis
    assertThat(
            computeTexts(
                res = InstrumentationRegistry.getInstrumentation().targetContext.resources,
                alarm =
                    create(
                        Calendar.getInstance().apply {
                          timeInMillis = now
                          add(Calendar.DAY_OF_YEAR, 3)
                        },
                        true,
                    ),
                now = now,
                prealarmDuration = 30,
            ))
        .isEqualTo("3 days\n30 minutes pre-alarm")
  }
  This code tells the alarm to go off in three days. This alarm is will play a prealarm milder sound for 30 minutes in order to gradually wake up the android user it was designed to serve. This code test is on lines 50-68 in the InfoFragmentTest.kt file.

- Code for a rocket targeting system.
https://github.com/Matt4tech/Parachute-Project <- Link to repository
https://github.com/Matt4tech/Parachute-Project/blob/master/MasterDevice <- Link to code location
void loop() {
  Serial.println("Start of loop");
  //GPS
  if(canGetGPSData()){
    latitude = getLat();
    longitude = getLong();
    gpsUpdated = true;
  }else{
    gpsUpdated = false;
  }
This code is constantly running in the rocket. It is constantly recieving and sending signals out to the computers running it. This code says that if the rocket can recieve GPS data from the satellites, then it will update its latitude and longitude data and send it directly to the computers running it. This code is on lines 71-80 in the MasterDevice file.

- File compression utility algorithm.
https://github.com/flto/linux/tree/a3a80255d58d0f0d304ba877ae0313a264973a70 <- Link to repository
https://github.com/flto/linux/blob/a3a80255d58d0f0d304ba877ae0313a264973a70/Makefile#L935 <- Link to the code location.
mod_compress_cmd = true
ifdef CONFIG_MODULE_COMPRESS
  ifdef CONFIG_MODULE_COMPRESS_GZIP
    mod_compress_cmd = gzip -n -f
  endif # CONFIG_MODULE_COMPRESS_GZIP
  ifdef CONFIG_MODULE_COMPRESS_XZ
    mod_compress_cmd = xz -f
  endif # CONFIG_MODULE_COMPRESS_XZ
endif # CONFIG_MODULE_COMPRESS
export mod_compress_cmd

# Select initial ramdisk compression format, default is gzip(1).
# This shall be used by the dracut(8) tool while creating an initramfs image.
#
INITRD_COMPRESS-y                  := gzip
INITRD_COMPRESS-$(CONFIG_RD_BZIP2) := bzip2
INITRD_COMPRESS-$(CONFIG_RD_LZMA)  := lzma
INITRD_COMPRESS-$(CONFIG_RD_XZ)    := xz
INITRD_COMPRESS-$(CONFIG_RD_LZO)   := lzo
INITRD_COMPRESS-$(CONFIG_RD_LZ4)   := lz4
# do not export INITRD_COMPRESS, since we didn't actually
# choose a sane default compression above.
# export INITRD_COMPRESS := $(INITRD_COMPRESS-y)

ifdef CONFIG_MODULE_SIG_ALL
$(eval $(call config_filename,MODULE_SIG_KEY))

mod_sign_cmd = scripts/sign-file $(CONFIG_MODULE_SIG_HASH) $(MODULE_SIG_KEY_SRCPREFIX)$(CONFIG_MODULE_SIG_KEY) certs/signing_key.x509
else
mod_sign_cmd = true
endif
export mod_sign_cmd

ifdef CONFIG_STACK_VALIDATION
  has_libelf := $(call try-run,\
		echo "int main() {}" | $(HOSTCC) -xc -o /dev/null -lelf -,1,0)
  ifeq ($(has_libelf),1)
    objtool_target := tools/objtool FORCE
  else
    SKIP_STACK_VALIDATION := 1
    export SKIP_STACK_VALIDATION

This code is on lines 914-954 in the file Makefile. It compresses a file if the mod_compress command is entered. If it equals true then it is entered and the code starts runnning to compress the file into different file types. This code is used in the Linux operating system which is a system that many computer users use similar to Windows or IOS.
 
- Weather forecasting algorithm.

- E-commerce checkout system process.

- Social media post scheduler.

- Fitness app calorie counter.

- Online voting system mechanics.

- Automated email response system.


## Submission Format

Document Title: "Exploring Code in Daily Life"
Content Structure: For each of the nine blurbs, include a heading with the blurb title, followed by your findings (link and line numbers) and a brief description. Also, do the same for 3 kinds of tools you use every day (for example: how the email app knows there are new messages, how my calendar adds new items, how my video game authenticates my user/password)
Length: No more than two paragraphs per blurb.
Evaluation Criteria
Accuracy: Correctly identifying relevant sections of code.
Clarity: Clear and concise descriptions of how the code functions.
Research Skills: Ability to effectively use online resources like GitHub.
