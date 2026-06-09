### Project 18 Beating Heart

**1. Description**

In this project, a beating heart will be presented via an Arduino board, a 8X8 dot matrix display, a circuit board and some electronic components. By programming, you can control the beating frequency, heart dimension and its brightness. 

**2. Wiring Diagram**

![](media/B24.png)

**3. Test Code**

1. Drag the two basic blocks. 

2. Initialize the dot matrix display. Set the CS pin to IO15 and its brightness to 3. Put these two executions between the basic blocks.

The following executions are all in "forever" block.

3. Clear the display. Control the display to draw lines and establish coordinates system and its origin as the following. Then, refresh the display to show the smaller heart with a delay of 1s. 

![](media/B25.png)

![](media/B26.png)

4. Repeat step 3 but draw lines as the picture below to show a bigger heart. 

![](media/B27.png)

![](media/B28.png)

**Complete Code:**

![](media/B29.png)

**4.  Test Result**

After connecting the wiring and uploading code, the two sizes of hearts are displayed alternately. 

![](media/B30.png)![](media/B31.png)

