# Fourth week

Now that I'm preparing for the fourth week, I want to start the homeworks & assignments. <br>
My fourth week's tasks are looking like that:

<img src="../img/week-4-1.png">

So my plan is to learn such things as:

- Chapter 2, with these labs: 2.2.3.4, 2.3.2.5, 2.4.1.2
- Chapter 6, with these labs: 6.4.1.3, 6.4.3.3, 6.4.3.4
- Finish an assignment
- Make a blog

Let's get on with it

<hr>

### Chapter two
In chapter two (Configure a Network Operating System) students of Suleyman Demirel university learned how to configure, access and also work with different OS (Operating Systems) on different intermediary devices.

#### 1. Cisco IOS (which is also known as Internetwork Operating System)

- Operating systems. There was a nice image of most common operating system architecture. Students of Suleyman Demirel University learned that top layer is **shell layer** which is closest to the end users and also is responsible for human/computer interactions. Can be implemented as a CLI also is known as Command Line Interface or GUI also is known as Graphical User Interface. **Kernel layer** is the most important part of OS (Operating System) that works directly with the hardware, to implement such things, top low-level programmers are writing hardware drivers in order to make computer know with what particular device it is working now and how to work with such concrete device.
- Purpose of OS (Operating System). CLI (which is also known as Command Line Interface) on cisco IOS (which is also known as Internetwork Operating System) enables to: use a keyboard to run CLI-based (which is also known as Command Line Interface) network programs, use a keyboard to enter text and text-based commands, view output on monitor.

#### 2. Cisco IOS (which is also known as Internetwork Operating System) Access

- Access methods. Three ways to access the device: **CLI** (which is also known as Command Line Interface) helps to access the device that you need to configure physically in such cases you will need to use console port, **SSH** (which is also known as Secure Shell) helps you to access the device that you need to configure not physically which means by the Internet or internet and since it is SSH (which is also known as Secure Shell) the connection between you and the device that you want to configure is secure, **telnet** helps you to access the device that you want to configure not physically which means the same as in the SSH (which is also known as Secure Shell) method by the Internet or internet however this method build a connection between you and the device that you want to configure in insecure way.

#### 3. Navigate the IOS (which is also known as Internetwork Operating System)

- Cisco IOS (which is also known as Internetwork Operating System) modes of Operation. CLI (which is also known as Command Line Interface) using console port and PuTTY.
- Primary command modes. **User EXEC mode** signatured by `'device-name'>`, in such mode consider you are in "READ ONLY" mode. **Privileged EXEC mode** signatured by `"device-name"#`, in such mode consider you are administrator.
- Configuration command modes. **Global configuration mode** signatured by `"device-name"(config)#`. **Line configuration mode** signatured by `"device-name"(config-line)#`, in which you can configure console, SSH, Telnet, AUX lines. **Interface configuration mode** signatured by `"device-name"(config-if)#`.
- Navigate between IOS (which is also known as Internetwork Operating System) modes. `enable/disable` to switch the modes. `"device-name"#configure terminal/exit` to enter global configuration. `"device-name"(config)#line "line-name"` to enter a line sub-configuration.
- Basic IOS (which is also known as Internetwork Operating System) command structure `switch>show ip protocols`

#### Other useful commands

- `"device-name"(config)# hostname "hostname"` - to rename the device
- `"device-name"(config)# enable secret "password"` - set password for Privileged mode
- `"device-name"(config-line)# password "password"` - set password for line
- `"device-name"(config)# service password-encryption` - encrypt all the passwords with light hash algorithm
- `"device-name"# show running-config` - show list of currently running configurations

### Chapter six

