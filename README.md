# Checkpoints
### How To Sync Quickly
##### Sync a fresh chain from 0 much quicker by loading "checkpoints" with your daemon.

### Setup

- Right click [this link](https://github.com/zumcoin/checkpoints/raw/master/checkpoints.csv) and choose `Save link as...` to download the latest checkpoints.csv.
- Place checkpoints.csv in the same folder as your ZumCoind daemon
- You can get ZumCoind from here if you don't have it already: https://latest.zumcoin.org
- Make sure you shut down any GUI wallets, or any other instances of ZumCoind.

### Usage

#### Windows

- First, open a command prompt in the same directory as ZumCoind.
- This can easily be done by moving to the ZumCoind directory in Windows Explorer, then typing `cmd` in the search bar and hitting enter:

- Finally, type `ZumCoind.exe --load-checkpoints checkpoints.csv` in the command prompt.

#### Linux, Apple

- First, open a command prompt in the same directory as ZumCoind.
- You can use the `cd` command to change to this directory. For example, `cd Downloads/zumcoin-vX.X.X`
- Alternatively, your file manager may provide the ability to open a terminal in your current directory. Navigate to the folder with ZumCoind in, and try right clicking, to see if you can open a terminal there:


- Finally, type `./ZumCoind --load-checkpoints checkpoints.csv` in the terminal.

### Expected Output

If you did the steps correctly, you should see something like this output.

```
2019-March-18 11:58:39.654478 INFO    Welcome to ZumCoin v0.5.0.1260 ()
2019-March-18 11:58:39.654914 INFO    Module folder: ZumCoind
2019-March-18 11:58:39.655249 INFO    Loading Checkpoints for faster initial sync...
2019-March-18 11:58:40.854979 INFO    Loaded 3000 checkpoints from checkpoints.csv
```

- ZumCoind will then start syncing from checkpoints.
- If you are using the CLI wallet, then you can just wait for it to finish syncing, and open your wallet.
- If you are using a GUI wallet, let it finish syncing, close it down by typing `exit` in the window, then open your GUI wallet.

### Common Errors

#### Invalid checkpoint file format

```
2019-March-18 12:10:08.325056 INFO    Loading Checkpoints for faster initial sync...
2019-March-18 12:10:08.339667 ERROR   Invalid checkpoint file format
2019-March-18 12:10:08.341758 ERROR   Exception: Failed to load checkpoints
```

- If you see output like the above, the file you are opening is either not a .csv file, or hasn't been downloaded correctly.
- Ensure you downloaded the file by right clicking, and choosing `Save link as...`.
- If you incorrectly chose the wrong file, you can accidentally  download a html page instead.
- When you open up the file, it should have lots of lines like this:

```
0,6552ad000960af5a5f6b032b7b9b711e9014e3f08724c44525e104768b9a0c00
1,a891830925a4695180e3a20166c4fba32077671e92e4d85efa50b9f94966dbca
2,944d0a0ed714716c545cc89999d43a90dab12848f467b70bead52cfed4ed3d93
```

- If you absolutely can't get it working, you can make a new text file, copy all the content from here into it: https://raw.githubusercontent.com/zumcoin/checkpoints/master/checkpoints.csv
- Then save as checkpoints.csv (Select filetype: all files in windows)

#### Failed to load checkpoints

```
2019-March-18 12:14:57.544286 INFO    Loading Checkpoints for faster initial sync...
2019-March-18 12:14:57.544569 ERROR   Could not load checkpoints file: checkpoints.csv
2019-March-18 12:14:57.544823 ERROR   Exception: Failed to load checkpoints
```

- If you see output like the above, it means the file isn't present in the directory you are in.
- Make sure you have placed the checkpoints.csv file in the same directory as ZumCoind.

#### ZumCoind.exe is not recognized / No such file or directory

```
C:\Users\yourUserName>ZumCoind.exe --load-checkpoints checkpoints.csv
'ZumCoind.exe' is not recognized as an internal or external command,
operable program or batch file.
```

`bash: ./ZumCoind: No such file or directory`

- If you see output like one of the above, it means your terminal isn't in the same folder as the ZumCoind program.
- You can type `pwd` to see what folder you are currently in.
- Try following the steps above to get into the right folder, then try again.
- If you type `ls`, you should see the ZumCoind program, if you are in the correct folder:

```
[zumcoin-vX.X.X]λ ls
miner  zumwallet  ZumCoind  zum-service
```

#### IO error

```
2019-March-18 11:58:40.857058 INFO    Opening DB in /home/user/.ZumCoin/DB
2019-March-18 11:58:40.858174 ERROR   DB Error. DB can't be opened in /home/zach/.ZumCoin/DB. Error: IO error: While lock file: /home/zach/.ZumCoin/DB/LOCK: Resource temporarily unavailable
2019-March-18 11:58:40.873692 ERROR   Exception: IO error
```

- If you see output like the above, something else has got the database open already.
- Make sure you have closed down any other ZumCoind's, GUI wallets, and walletd.
- Use a task manager to help you find any which might be running in the background, then try again.
