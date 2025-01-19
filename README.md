# Things to do with a Raspberry Pi 5 16G

List of things to do with a RPi5 16GB

## Get the hardware

Buy:

1. One Raspberry Pi 5 16GB.
2. One Raspberry Pi Power Supply. It's best to buy the original.
3. One SDCard. 32GB is enough if you want to upgrade with a NVME disk later. Otherwise, the larger, the better.

Buy these, if you want to:

1. A case/enclosure. Make sure it will fit with whatever NVME upgrade you plan to get.
2. A cooling solution. A RPi5 will slow down, if not cooled enough. You can live with the cooler from the Raspberry Pi case, but the the RaspberryPi5 cooler allows for better cooling and even overclocking.

## Install a Operating System

I recommend to install Raspberry Pi OS, the original. Install to a SDCard first, then update everything, including the firmware on your RaspberryPi, after that install to NVME. This is to make sure the Raspberry Pi has the highest level of compatibility.

1. Install Raspberry Pi OS to SDCard: https://www.raspberrypi.com/software/
2. Connect a Keyboard, Mouse and Display
3. Get network access:
4. Update the system and firmwares.

## Install a NVME disk

Buy:

1. A NVME board. There are plenty out there. I would say make sure it can hole NVME of the size 2280, then you can buy whatever NVME you want in terms of size. I got the Pimoroni board.
2. A NVME SSD. I recoomend to buy at least 1TB, as they are cheap. Mine is a WD Blue SN570 1TB.

## Overclock and Benchmark the system

Download the benchmark:

1. Go to https://www.geekbench.com/preview/
2. Download the Aarch64 link:

        wget $(wget -O - -q https://www.geekbench.com/preview/ | awk -F\" '/a href.*AArch64/{print $4}')

3. Unpack the archive:

        tar xzvf Geekbench-*.tar.gz

4. Change directory and run the benchmark:

        cd Geekbench-*-LinuxARMPreview/ ; ./geekbench6 --cpu

5. Review the results with the provided URL.

To overclock you can add this line to /boot/firmware/config and reboot, try 100 MHz more, then reboot and run the benchmark. If the machine seems stable, add 100MHz more. Once the benchmark fails or the machine gets unstable, reduce by 100MHz:

    # default is arm_freq=2400
    arm_freq=2500

Once you have a stable overclock, compare the benchmark result with your old one by pasting the benchmark ID number into the Geekbench URL:
https://browser.geekbench.com/v6/cpu/compare/10000904?baseline=10000613

10000613 is my unoverclocked benchmark. 10000613 is my 200MHz overclocked benchmark.

## Run a local AI-Chatbot: ollama

We do the next steps as root. Type sudo -i to get a root shell. Then:

1. Install ollama:

        curl -fsSL https://ollama.com/install.sh | sh

2. Download a suitable model:

        ollama pull llama3.2

3. Run the model like a chat:

        ollama run llama3.2

4. Run the model like a benchmark:

        ollama run llama3.2 "What are things one can do during a visit to Duisburg, Germany?" --verbose

We can install a ChatGPT style webinterface now.

## Install Docker and Portainer

## Install open-webui

## Install DNS with Adblock: Pihole

## Configure Filesharing
