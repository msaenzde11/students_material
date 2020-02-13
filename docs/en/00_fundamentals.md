# Prework

# How the web works

To start with the course, let's do a very simple assignment. We're going to encourage you to watch these videos:

- [How the Internet Works for Developers - Pt 1 - Overview & Frontend](https://www.youtube.com/watch?v=e4S8zfLdLgQ&t=5s)
- [How the Internet Works for Developers - Pt 2 - Servers & Scaling](https://www.youtube.com/watch?v=FTAPjr7vgxE)

Don't worry if some concepts are strange to you (they surely will), we'll be talking about them throughout the course. Just make sure that you kind of understand concepts like HTTP protocols or how HTML&CSS works.

# Front-End developer

A front-end web developer is responsible for implementing visual and interactive elements that users engage with through their web browser when using a web application. They are usually supported by back-end web developers, who are responsible for server-side application logic and integration of the work front-end developers do. (1)

<img src='assets/what-is-front-end-dev.png'></img>

The objective of designing a site is to ensure that when the users open up the site they see the information in a format that is easy to read and relevant. This is further complicated by the fact that users now use a large variety of devices with varying screen sizes and resolutions thus forcing the designer to take into consideration these aspects when designing the site. They need to ensure that their site comes up correctly in different browsers (cross-browser), different operating systems (cross-platform) and different devices (cross-device), which requires careful planning on the side of the developer. (2)

* (1) [Front-End Web Developer Job Description Template](https://www.toptal.com/front-end/job-description)
* (2) [What Is a Front-End Developer? · Front-End Developer Handbook 2018](https://frontendmasters.com/books/front-end-handbook/2018/what-is-a-FD.html)
 
## Front-End Jobs Titles (3)
Below is a list and description of various front-end job titles. The common, or most used (i.e., generic), title for a front-end developer is, "front-end developer" or "front-end engineer". Note that any job that contains the word "front-end", "client-side", "web UI", "HTML", "CSS", or "JavaScript" typically infers that a person has some degree of HTML, CSS, DOM, and JavaScript professional know how.

**Front-End Developer**
The generic job title that describes a developer who is skilled to some degree at HTML, CSS, DOM, and JavaScript and implementing these technologies on the web platform.

**Front-End Engineer (aka JavaScript Developer or Full-stack JavaScript Developer)**
The job title given to a developer who comes from a computer science, engineering, background and is using these skills to work with front-end technologies. This role typically requires a computer science degree and years of software development experience. When the word "JavaScript Application" is included in the job title, this will denote that the developer should be an advanced JavaScript developer possessing advanced programming, software development, and application development skills (i.e has years of experience building front-end applications).

**CSS/HTML Developer**
The front-end job title that describes a developer who is skilled at HTML and CSS, excluding JavaScript and Application know how.

**Front-End Web Designer**
When the word "Designer" is included in the job title, this will denote that the designer will posses front-end skills (i.e., HTML & CSS) but also professional design (Visual Design and Interaction Design) skills.

**Web/Front-End User Interface (aka UI) Developer/Engineer**
When the word "Interface" or "UI" is included in the job title, this will denote that the developer should posses interaction design skills in addition to front-end developer skills or front-end engineering skills.

**Mobile/Tablet Front-End Developer**
When the word "Mobile" or "Tablet" is included in the job title, this will denote that the developer has experience developing front-ends that run on mobile or tablet devices (either natively or on the web platform, i.e., in a browser).

**Front-End SEO Expert**
When the word "SEO" is included in the job title, this will denote that the developer has extensive experience crafting front-end technologies towards an SEO strategy.

**Front-End Accessibility Expert**
When the word "Accessibility" is included in the job title, this will denote that the developer has extensive experience crafting front-end technologies that support accessibility requirements and standards.

**Front-End Dev. Ops**
When the word "DevOps" is included in the job title, this will denote that the developer has extensive experience with software development practices pertaining to collaboration, integration, deployment, automation, and measurement.

**Front-End Testing/QA**
When the word "Testing" or "QA" is included in the job title, this will denote that the developer has extensive experience testing and managing software that involves unit testing, functional testing, user testing, and A/B testing.

* (3) [Front-End Jobs Titles · Front-End Developer Handbook 2018](https://frontendmasters.com/books/front-end-handbook/2018/practice/types-of-front-end-dev.html)

## Making a Front End Developer (4)

<img src='assets/makingFED.png'></img>

* (4) [How FDs Are Made · Front-End Developer Handbook 2018](https://frontendmasters.com/books/front-end-handbook/2018/practice/making-fd.html)

Now let's see how you can speed up your development with the Command Line Interface.

# The command line or terminal interface

Believe it or not, before the world of windows, tabs, docks and menu bars, the only way to interact with a computer was through the command line. Even today there are a lot of powerful actions you can perform by just typing things into a terminal prompt. It’s like an instant messaging system between you and your computer!

## Essential Unix commands

You will be using these constantly from this point on, so feel free to print them out on a cheat sheet.

### ls

- **What it does**: List files.
- **Detail**: If you don't provide a folder it will look in the current folder. Often it's useful to see the list in a vertical format. You can do that using the `-l`. option. Also sometimes you need to see the hidden files. Use `a` option.
- **Examples**:
  - `ls stuff/`: list contents of the `stuff/` folder.
  - `ls -alh`: list contents of the current directory vertically, including hidden ones.

### cd

- **What it does**: Change into another directory.
- **Detail**: Can go up one level in the directory tree by using `..`.
- **Examples**:
  - `cd stuff/`: Change to the stuff/ directory.
  - `cd ..`: Go up one level.
  - `cd ../../other`: Go up two levels and change to the other directory.

### mkdir

- **What it does**: Create an empty directory.
- **Detail**: Can use `-p` option to make multiple sub-directories quickly.
- **Examples**:
  - `mkdir stuff`: Create the `stuff/` directory.
  - `mkdir -p work/mfr/assignment1`: Create the `work/` with `mfr/assignment1` directories inside.

### rm

- **What it does**: Remove a file or directory.
- **Detail**: Use `-r` option for deleting directories.
- **Examples**:
  - `rm file.txt`: Delete the `file.txt` file.
  - `rm -rf work/mfr/assignment1`: Delete the `work/mfr/assignment1` directory.

### cp

- **What it does**: Copy a file or directory.
- **Detail**: Takes two parameters: source and destination. Can use wildcard in source `*` to copy files that match a pattern. Use `-r` option for directories.
- **Examples**:
  - `cp program.js app.js`: Copies `program.js` to `app.js`.
  - `cp stuff/*.html html-files/`: Copies all files in `stuff/` that end in `.html` into - the `html-files/` folder.
  - `cp stuff/ stuff-copy`: Copies the `stuff/` directory as the `stuff-copy/` directory.

### mv

- **What it does**: Move and/or rename a file or directory.
- **Detail**: Takes two parameters: source and destination. Can use wildcard in source `*` to move files that match a pattern. If the destination is a folder, it will move the files into the folder and leave the file's name unchanged.
- **Examples**:
  - `mv program.js app.js`: Renames `program.js` to `app.js`.
  - `mv program.js stuff/`: Moves `program.js` into `stuff/`.
  - `mv stuff/*.html html-files/`: Moves all files in `stuff/` that end in `.html` into the `html-files/` folder.

### touch

- **What it does**: Create a new empty file.
- **Detail**: Takes one parameter, the name of the file. You can create multiple files at once by putting more than one name.
- **Examples**:
  - `touch newfile.txt`
  - `touch file1.txt file2.txt file3.txt`

### open

- **What it does**: Open a file or directory.
- **Detail**: Takes one parameter file or folder to open. If we don't specify an app it will open the file with the default application for that file-type. We can choose the program we want to use adding `-a appName` between `open` and `filename`. We can also open more than one file at a time concatenating files.
- **Examples**:
  - `open myFile1`: Opens myFile1
  - `open myDirectory`: Opens myDirectory
  - `open myFile1 myFile2 myFile3`: Opens myFile1, myFile2 and myFile3
  - `open -a appName myFile1`: Opens myFile1 with appName
  - `open .`: Opens current directory

### pwd

- **What it does**: Show the current directory.
- **Detail**: Short for *print working directory*, not password (I know!). Doesn't take any options, just use it as-is to remind yourself where you are.
- **Examples**:
  - pwd

## Exercises

- Print the name of the folder you’re in
- Show a list all of the files that are in this folder
- Make a new folder and call it `madrid_for_refugees`
- Inside your `madrid_for_refugees` folder, make a new folder called `Projects`
- Go back to the `madrid_for_refugees` folder and make another folder called `Exercises`
- Inside the `Exercises` folder, make a new file called `first.txt`
- Open `first.txt`
- Create two more files called `second.txt` and `third.txt`
- Show a list of all the files in this folder
- Move `second.txt` to your `Projects` folder
- In your `Exercises` folder, rename the `third.txt` file to `second.txt`
- Copy the `first.txt` file from your `Exercises` folder to your `Projects` folder
- Go to your `Projects` folder and delete all the files
- Delete the `Projects` directory

If you feel like this is too little for you, take a look at [this github repository](https://github.com/scottjoseph/cmd-exercises) full of cli exercises!
