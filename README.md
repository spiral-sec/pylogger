# PyLogger
In this Workshop you 'll learn :

:heavy_check_mark: How to spy on all the keystrokes of a computer

:heavy_check_mark: How to send it to a remote server

:heavy_check_mark: How to transform a .py in a binary with Pyinstaller

:heavy_check_mark: How to obfuscate such a binary

## Step 0 : Setup
Please follow the steps in the [SETUP.md](./SETUP.md) file.

## Step 1 : Get the keystrokes

First things first, make some researches about how can you retrieve the keystrokes in any process.
Don't forget to search for python code.

> :bulb: To test your program, you can either print the keystrokes on your terminal, or write it in a file.

You will notice that some characters may appear in a strange way due to keyboard configuration.
Fix it.

- [ ] Get the input on any active process
- [ ] Transform the character to make it completely readable

## Step 2 : TCP server

### TCP / IP

You are now very sure that the program works? Great!

If it works on your machine, it can certainly work on your victim's. However, in order to retrieve
it, you can code a quick TCP server with [socketserver]() library.

- [ ] Code a server that will send requests on the victim side
- [ ] Code a client that will listen to requests on the hacker side that will prettify and print
the received input

> :bulb: for the sake of the Workshop, we are going to provide you a remote server and its IP address.

### Finishing touches

Your communication is pretty ok, but not secure at all. What happens if you receive several requests
at the same time? Or you have infected several victim, your weak server wouldn't be able to handle it.

- [ ] Use python [threads]() to target the function where you handle the listening of your requests
- [ ] Encrypt your communication with AES.
- [ ] Decrypt it on the client side.

## Step 3 : Pyinstaller

> Pyinstaller is a python tool that will convert your python script into a binary.
> **Why do I need to do that?** - Because if the victim discovers your script,
> He/She will know exactly what you are trying to do, and how you are doing it, 
> and worst: how to stop it.

### Installation
in your terminal, run :
```bash
pip3 install pyinstaller
```

You can read [this](https://pyinstaller.readthedocs.io/en/stable/usage.html) documentation to know how to do it.

- [ ] Run pyinstaller on the victim script, and name it `pylogger`.

## Step 4 : Basic Obfuscation

### [What is obfusation ?](https://en.wikipedia.org/wiki/Obfuscation_(software))

### Step 1

When you run the `nm` commmand on your binary, you must notice a huge number of lines describing all the functions that your program calls.
It is bad : we don't want smart reverse engineer guys to understand exactly how our program works.

To do so, find a way to get this output :
```sh
nm: pylogger: no symbols
```

### Step 2

Now that you removed the symbols of your binary, get this very minimal output:

```sh
ransom:     file format elf64-x86-64
architecture: i386:x86-64, flags 0x00000102:
EXEC_P, D_PAGED
start address 0x0000000000469cd8
```

and nothing else !!

with the command:
```sh
$ objdump -fs pylogger
```

Difficult huh ? Make some researches ^^

### Step 3

Wow ! You have made it so far !
I don't know what did you use for accomplish the previous step, but make sure no clue can appear when use a simple `strings` command on your ransomware...

### Step 4

Ok, what we have made is cute but... We can always try to debug the program.
You can:
* implement a `sigaction` that will make `SIGTRAP` useless
* terminate the program each time we call a debugger on it.

Congratulations !

## Going further