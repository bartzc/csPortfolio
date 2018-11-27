# csPortfolio


  
  <details><summary><strong>Web Page</strong></summary>
    <p>
      <a href="https://bartzc.github.io/bartzPhotography/websiteMain.html">Link<a>
    
  >The web page assignment allowed for me to develop an understanding for html and overall web development.
    </p>
  </details>
  <details><summary><strong>Lightning</strong></summary>
    <p>
     <a href="https://bartzc.github.io/lightning2/">Link<a>
       
   >Lightning helped refresh my knowledge of processing, random, positioning and more.
    </p>
  </details>
  
  <details><summary><strong>Dice</strong></summary>
    <p>
     <a href=https:"//bartzc.github.io/dice3/index.html">Here<a>
           
   >Dice taught me OOP (Object Oriented Programming) techniques and creating an appealing interface.
    </p>
  </details>
  <details><summary><strong>Dice JS</strong></summary>
    <p>
     <a href="https://bartzc.github.io/dice3/index2.html">Here<a>
       
   >Converting my Dice program to javaScript allowed me to learn the beginnings of javaScript, and it's own methods/operations.
    </p>
  </details>
  <details><summary><strong>Chemotaxis</strong></summary>
    <p>
      <a href="https://bartzc.github.io/chemotaxis4/">Here<a>
            
   >Chemotaxis allowed me to become more refreshed with Math.random and positioning/movement. The java version doesn't work due to an arrayList error that occurs, the javaScript version is not fully done yet.
    </p>
  </details>
  <details><summary><strong>StarField</strong></summary>
    <p>
      <a href="https://bartzc.github.io/starfield5/">Here<a>
            
   >StarField was an expierence. This project was a place for me to use many of the techniques I have learned over the tri and experiment with them all in my own way. StarField also taught me more about interfaces and inheritance.
    </p>
  </details>
  <details><summary><strong>College Presentation</strong></summary>
    <p>
      <a href="https://bartzc.github.io/collegePresi/file.html">Here<a>
            
   >The college presentation was an oppertunity to explore my options for future endevores at *Gustavus/St. Olaf*.
    </p>
  </details>

# QnA


1. Reflect on all your portfolio projects.  
>With all my lab links.

2. What is one or two things that are a source of pride in your programming development?  
>My space Invaders game I created. Link to repo:(https://github.com/bartzc/spaceInvaders)
3. Identify them, write about why they are accomplishments, how you did it and what you learned.  Be sure to submit a code snippet along with your writing on the readMe file in your repo.
> In my Space Invaders game, I created many classes, often using things not taught in class until just now (Scanners and file readers). 

*The following code is an example of a leaderboard saved in a text file that is pulled up whenever the user goes into the leaderboard option:*
```Java


//Opening the board
        private ArrayList<leaderboards> hold = new ArrayList<leaderboards>(5);

  public ArrayList<leaderboards> pullList() {
    BufferedReader read = createReader("leaderboards.txt");
    String line;

    try {
      while ((line=read.readLine())!=null) {

        String [] pieces = split(line, "  ");
        String x = pieces[0];
        int y = int(pieces[1]);
        hold.add(new leaderboards(x, y));
      }
      read.close();
    } 
    catch(IOException e) {
      e.printStackTrace();
    }
    return hold;
  }
  
  
  
  //Saving the board
  public setBoard(ArrayList<leaderboards> l, String n, int s) {
    lead = l;
    name = n;
    score = s;
  }

  public void setPos() {
    for (int i = 9; i >0; i++) {
      if (lead.get(i).getScore()>score) {
        lead.add(i, new leaderboards(name, score));
      }
    }
  }
  public void write() {
    output = createWriter("leaderboards.txt");
    for (int i = lead.size(); i>=0; i--) {
      output.println(lead.get(i).getName()+"  "+lead.get(i).getScore());
    }
  }
  
  
```
4. Identify the most significant hurdle you encountered last trimester.  Write about what it was and how it was resolved.
>Last trimester the greatest hurdle I had was working on starfield. I was trying to create a controller for the velocity of the stars and had the diffuculty of the stars moving to fast and flying off the screen when I would adjust it at all. To solve this, I set boarders and linked the speeds together so that they wouldn't move to fast one way.
6. Describe the incremental and iterative development process of your included code, focusing on two distinct points in that process. Describe the difficulties and/or opportunities you encountered and how they were resolved or incorporated. In your description clearly indicate whether the development described was collaborative or independent. At least one of these points must refer to independent program development
>I found the most issues when trying to create the spaceship movement along with the arrayLists of objects. 
>1. This creates/checks the shots that the hero ship shoots by comparing the shots arrayList to the enemy ships array list. I found issues with this trying to avoid latency in the shots being checked and removing the ships once they were hit but worked around this by singling out just the shots and running lots of checks to create the 
```Java
		for (int i = shots.size()-1; i>=1; i--) {
      fill(0, 252, 0);
      rect(shots.get(i).getX(), shots.get(i).getY(), 5, 20);
      shots.get(i).incrY();
      color c = get(shots.get(i).getX()+10, shots.get(i).getY()-1);
      if (c == check) {


        for (int k = 0; k<shots.size()-1; k++) {
          for (int j = shipList.size()-1; j>=0; j--) {
            if ((shipList.get(j).getX()<shots.get(k).getX()+10&&shipList.get(j).getX()+50>shots.get(k).getX()+10)&&(shipList.get(j).getY()<=shots.get(k).getY()-1&&shipList.get(j).getY()+50>=shots.get(k).getY()-1)) {
              shipList.remove(j);
              shots.remove(k);
              finalScore +=20;
              shipCount--;
            }
          }
        }
```
> 2. When trying to create my spaceship movement and jumping down the lines of the game board I came across many issues with the positioning of the ships when the lead ship would reach their x axis max/min values. When that would occur the entire ship base would move down one line, but when that lead ship would be killed and erased from the arrayList, the max and min values would then be located off the screen. To solve this I created a check that would look at each end ship for the 5 rows of ships and then use the ship with the greatest/lowest x value in order to determine what ship should be the checker. 
```
public void update() {
    indexUpdate();
    for (int i = 0; i<shipList.size(); i++) {

      if (right==true) {
        shipList.get(i).decX(0);
        shipList.get(i).incrY(0);
        shipList.get(i).incrX(.75);

        if (shipList.get(far).getX()>=900) {
          right = false;
          left = true;
          down = true;
        }
      }
      if (left==true) {
        shipList.get(i).incrX(0);
        shipList.get(i).incrY(0);
        shipList.get(i).decX(.75);

        if (shipList.get(near).getX()<=40) {
          right = true;
          left = false;
          down = true;
        }
      }
    }
    if (down == true) {
      for (int j = 0; j<shipList.size(); j++) {
        shipList.get(j).incrY(10);
      }
      down = false;
    }
  }
  public void indexUpdate() {

    for (int i = 0; i<shipList.size(); i++) {
      if (far<shipList.size()&&shipList.get(far).getX()<shipList.get(i).getX()) {
        far = i;
      } else {
        far=shipList.size()-1;
      }
    }
    for (int i = 0; i <shipList.size(); i++) {
      if (near>shipList.size()&&shipList.get(near).getX()>shipList.get(i).getX()) {
        near = i;
      } else {
        near = 0;
      }
    }
		
```
# Code From This Year

> Code I found most *challenging* this year was from starfield. In the following code segment, I created a gui for the x and y axis velocity. The gui wasn't actually diffucult to do, but I found the interaction between the user and the code intresting and creating the individual methods in the gui class.
```Java
//All methods that make up the gui class
void buttons() {
    rectMode(CORNER);
    fill(255, 75);
    rect(0, 0, 200, 1440);
    //xVel controller
    fill(255);
    rect(90, 250, 20, 400);
    textSize(45);
    text("xVel:", 45, 150);
    textSize(35);
    text("\'1\' to reset", 5, 780);
    fill(255, 85);
    textSize(32);
    text("FASTEST", 35, 220);
    text("SLOWEST", 35, 700);
    //yVel controller
    fill(255);
    rect(90, 950, 20, 400);
    textSize(45);
    text("yVel:", 45, 850);
    fill(255, 85);
    textSize(32);
    text("FASTEST", 35, 920);
    text("SLOWEST", 35, 1400);


    //Sliders should follow mouse when pressed on button. 
    fill(0, 1, 0);
    rectMode(CENTER);
    rect(100, followMouse1, 100, 40);
    rect(100, followMouse2, 100, 40);
    if (mousePressed||keyPressed) {
      checker();
    }
  }
  void checker() {

    color mouse = get(mouseX, mouseY);
    //top scroller
    if (box == mouse&&mouseY<=650&&mouseY>=250) {
      if (mouseY>followMouse1) {
        followMouse1+=2;
      }
      if (mouseY<followMouse1) {
        followMouse1-=2;
      }
    }//Bottom Scroller
    if (box == mouse&&mouseY<=1350&&mouseY>=950) {
      if (mouseY>followMouse2) {
        followMouse2+=2;
      }
      if (mouseY<followMouse2) {
        followMouse2-=2;
      }
    }

    if (keyPressed) {
      if (key == '1') {
        followMouse1 = 450;
        followMouse2 = 1150;
      }
    }
  }
  int topScroll() {
    return followMouse1;
  }
  int bottomScroll() {
    return followMouse2;
  }
  ```
  <sub><sup>*Congrats on completing tri 1 guys!*</sup></sub>
