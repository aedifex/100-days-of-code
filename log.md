# 100 Days Of Code - Log

### Day 0: May 11, 2021

**Today's Progress:** Worked on a few simple exercises to get back into the groove of programming. I'm trying to improve my understanding of data structures, algorithms, and good software development practices.

**Thoughts:** Algorithms are challenging for me. I find that practicing and at times drawing out a sequence of steps / events can be highly beneficial. Seriously. Just mapping out the general "flow" of a program, or visualizing a representation of elements can be a great help! Practice makes perfect.

### Day 1: May 12, 2021

**Today's Progress:** Continued to work on some basic sorting algorithms. Concluded a "simple" exercise on sanitizing user input in the form of a comma separated list of integer values.

**Thoughts:** Thinking about ways to improve performance and make the code cleaner, perhaps adding a helper function or two?

### Day 2: May 13, 2021

**Today's Progress:** More work on sanitizing user input. An almost ubiquitous exercise, yet something that can prove deceptively challenging. In fact, lack of good input validation is the cause of countless bugs and exploits.

**Thoughts:** While input validation and basic sorting algorithms are first year CS stuff, they can still be very tricky. However! It's imperative to have a firm grasp of the "basics" as a software engineer.

### Day 3: May 14, 2021

**Today's Progress:** Finally completed the rPi assignment! I built a simple temperature sensor using a breadboard, a simple senor itself, and wrote a nifty python program to read and interpret data. Definitely a great exercise in putting together multiple components and using a high level language to derive meaning from the data.

**Thoughts:** I have a few ideas for rPi / breadboard projects moving forward. More to come!

### Day 4: May 15, 2021

**Today's Progress:** Working on creating a Git repo with all of my terminal / vim / sublime text configuration and automating the setup of these environments.

**Thoughts:** Getting deep into the nuances of the tools we use. Thankfully, most of these tools have simple configuration files that can be easily ported to a VCS system.

### Day 5: May 16, 2021

**Today's Progress:** Created a tic-tac-toe python program! Spent a little time debugging a few of the errors.

**Thoughts:** "*[1,2,3,4,5,6,7,8,9]" was a cool hack - basically destructured the list into individual elements.

### Day 6: May 17, 2021

**Today's Progress:** Concluded another round of input sanitation.

**Thoughts:** Thinking about how this would look in C. Conceptually very similar, though the mechanics would be a bit more involved.

### Day 7: May 18, 2021

**Today's Progress:** Circled back to the terminal setup. Made a ton of progress, though getting the backup && restore fully automated requires a bit more heavy lifting.

**Thoughts:**

### Day 8: May 19, 2021

**Today's Progress:** Still hacking on ^^

**Thoughts:**

### Day 9: May 20, 2021

**Today's Progress:** Setup and configured a sandbox AWS environment. Spun up an instance, configured a basic security group.

**Thoughts:**

### Day 10: May 21, 2021

**Today's Progress:** More time on the sandbox AWS account.

**Thoughts:**

### Day 11: May 22, 2021

**Today's Progress:**

**Thoughts:**

### Day 12: May 23, 2021

**Today's Progress:**

**Thoughts:**

### Day 13: May 24, 2021

**Today's Progress:**

**Thoughts:**

### Day 14: May 25, 2021

**Today's Progress:**

**Thoughts:**

### Day 15: May 26, 2021

**Today's Progress:**

**Thoughts:**

### Day 16: May 27, 2021

**Today's Progress:**

**Thoughts:**

### Day 17: May 28, 2021

**Today's Progress:**

**Thoughts:**

### Day 18: May 29, 2021

**Today's Progress:**

**Thoughts:**

### Day 19: May 30, 2021

**Today's Progress:**

**Thoughts:**

### Day 20: May 31, 2021

**Today's Progress:**

**Thoughts:**

### Day 21: June 1, 2021

**Today's Progress:**

**Thoughts:**

### Day 22: June 2, 2021

**Today's Progress:**

**Thoughts:**

### Day 23: June 3, 2021

**Today's Progress:**

**Thoughts:**

### Day 24: June 4, 2021

**Today's Progress:**

**Thoughts:**

### Day 25: June 5, 2021

**Today's Progress:**

**Thoughts:**

### Day 26: June 6, 2021

**Today's Progress:**

**Thoughts:**

### Day 27: June 6, 2021

**Today's Progress:**

**Thoughts:**

### Day 28: June 7, 2021

**Today's Progress:** Nomad. Dusted the cobwebs off of an old OSS project that provisions a local cluster of machines for testing Nomad, a delightful hashicorp tool.

**Thoughts:** This is a fun project, definitely getting into the weeds technically, which is good!

### Day 29: June 8, 2021

**Today's Progress:** Needed to rebuild the Vagrant environment, there were some errors in the Vagrantfile plus the VM images were outdated. Several odd errors were introduced into the environment which was vexing...

**Thoughts:** Finally signed up for Stackoverflow...After all these years.

### Day 30: June 9, 2021

**Today's Progress:**

**Thoughts:**

### Day 31: June 10, 2021

**Today's Progress:**

**Thoughts:**

### Day 31: June 11, 2021

**Today's Progress:** Worked with Menno yesterday during "happy hour" at work. He suggested updating the box/vm in the Vagrantfile to something newer - e.g. bionic64. Alas, somehow, this did the trick! Which is somewhat shocking...given the "other" box worked in a different environment. Thankfully, we have a functional environment! Now it's time to layer on some additional tooling and automate the hell out the setup. My intention is to have a lightweight environment myself and others on my team can use to experiment with a dope technology (Nomad).

**Thoughts:** How did the original VM work in one environment, with nearly identical configuration? Whereas updating the box changed this vexing issue?

### Day 31: June 12, 2021

**Today's Progress:** Moar progress on the cluster. I'm using a combination of a Makefile with a simple shell script to setup and execute the config files needed for the agent, and rather than manually passing the private IP for the host, use a simple envar passed via Vagrant file.

**Thoughts:**

### Day 32: June 13, 2021

**Today's Progress:** Follow up on the Vagrant environment - finally was able to inject dynamic variables into the VM's from the Vagrantfile.

**Thoughts:**

### Day 33: June 14, 2021

**Today's Progress:** Got the cluster fully operational. Using a Makefile & script to automate parts of the setup. Ran a small sample job that leverages the docker provisioner. Really exciting stuff.

**Thoughts:**

### Day 33: June 15, 2021

**Today's Progress:** Running jobs in the Nomad env.

**Thoughts:**

### Day 34: June 16, 2021

**Today's Progress:** Tons. Used a system job to orchestrate and deploy the Lacework agent to one of the nodes.

**Thoughts:** Levant files are a tool used to help templatize Nomad job files
https://github.com/hashicorp/levant

Within the Nomad job declaration, we're mounting these volumes between the container and host OS.

```
config {
        image = "lacework/datacollector:3.7.2"
        privileged = true
        volumes = [
          "/var/lib/lacework:/var/lib/lacework",
          "/var/log:/var/log",
          "/var/run:/var/run",
          "/etc/passwd:/etc/passwd:ro",
          "/etc/group:/etc/group:ro",
          "/:/laceworkfim:ro"
        ]
      }
```

We also needed to update the client config for Nomad
```
options {
        docker_volumes_enabled = true
    }
```
to enable docker volumes.

And lastly:

```
plugin "docker" {
  config {
    allow_privileged = true
    volumes {
      enabled = true
    }
  }
}
```

Questions:

1. What are volumes?

Well, storage. Grouped into physical blocks, partitions, and external devices. When interacting with VMs and containers, things get interesting.

2. What is volume mounting?

Follow up question - difference between mounting data volumes versus mounting host volumes?

3. What are docker volumes?

"Docker volumes are file systems mounted on Docker containers to preserve data generated by the running container.

The volumes are stored on the host, independent of the container life cycle. This allows users to back up data and share file systems between containers easily."

4. What is a privileged docker user?

"Docker privileged mode grants a Docker container root capabilities to all devices on the host system. Running a container in privileged mode gives it the capabilities of its host machine.""

https://www.nomadproject.io/docs/drivers/docker#docker-privileged-enabled

https://www.nomadproject.io/docs/drivers/docker#volumes

"allocation working directory"? Need to review this.

### Day 35: June 17, 2021

**Today's Progress:**

**Thoughts:**

