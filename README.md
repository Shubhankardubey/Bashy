# Bashy
Learning the bash commands in fun way.

Bashy: Online bash terminal(emulator) tutorial
Check out the site live at -->  lterm	Gitter

Bashy is an online Terminal Eminulator. It is a step by step tutorial that will teach you the bash commands by making you execute them.

Nothing is better than learning by doing.

It is fully online and doesn't require any extra shitty access. Being an emulator, it only virtualizes a terminal environment and so the commands executed doesn't effect either the server or your local machine.

List of commands available presently
echo-----[To display a string]
pwd------[Shows you the present working directory]
ls-------[Lists all the files]
cd-------[To change directory - change the current working directory to a specific directory]
cd ..-----[Moves you up one directory(parent)]
cat------[Concatenate and print the content of files]
clear----[Clears the terminal screen]
touch----[Changes file timestamps or creates a new file]
cp/mv--[To copy/move files]
rm-------[Delets a file/directory]
uname----[Shows the name of the Linux/Unix system you are using]
data-----[Shows the local standard date & time]
ifconfig-[Shows information about active network interfaces.]
mkdir----[Creates a new directory]
tty------[Prints the file name of the terminal connected to standard input]
history--[Shows all the commands which are used in the previous iterations]
List of commands that can be added
export
less
more

You can also make terminal tutorials of various technologies.

To add your new commands
edit the file main.js to add your commands.
You don't have to worry about any other files or programs.
If a command doesn't need further steps:
// without argument
ls: function() {
        this.echo('This is the ls command\n');
}
// with argument
echo: function(arg1) {
        this.echo('This is the echo command' + arg1 + '\n');
}
If a command needs further steps:
cd: function(arg1) {
	this.push(function(cmd, term) {
                if(cmd == 'another_command')
                    this.echo('another_command');
		}, {
                    prompt: '[[b;#44D544;]lterm@localhost/' + arg1 + ':~$] ',
                   }
        );
}
IMPORTANT

On addition of a new command, increase the size of arr array. This array acts like a counter to check if a task/command is completed or not.
You need to add the new command into the second array arr2 . This array stores all the commands and helps in fetching the completed commands when the history command is executed.
Please make sure that you do not alter the positions of commands in arr2, You need to add the new command towards the last.
Example: If I add the command - echo. I will add another 0 to the end of arr. Then I will make arr[index] = 1 under echo command.
var arr = [0,0,0,0,0,0,0,0,0,0,0,0,0,0]; // Will add another 0 here. The place where you added is the index.
var arr2 = ['list of all other commands']; // Will add the 'echo' command here
...
...
echo: function(arg1) {
            arr[index_where_you_added_0] = 1;	// Will make the value at that index to 1. 	
            this.echo(arg1 + '\n');
            this.echo('> The [[b;#ff3300;]echo] command prints back your arguments.');
            this.echo('> Type [[b;#ff3300;]help] and check your first task is completed.');
            this.echo('> Now type [[b;#ff3300;]pwd] to continue.');
},

If you face any problem or cannot understand anything, open up an issue.
You can also edit the readme and make it more user friendly to help out new contributers.

NOTE: Kindly keep the diplay of the terminal intact while making an update. A single extra space can make the look of the emulator little odd. So keep that in mind while printing something using echo command.
