# Software-Test-Automation

## Step 1: install web browser(Chrome, Firefox, Chromium)

My browser: Google Chrome 106.0.5249.119 

<img width="500" alt="image" src="https://user-images.githubusercontent.com/93315926/195972379-a8229c7e-aaf5-4eec-8c81-c55c428775e2.png">

How to check your Google Chrome version? <br>

<img width="500" alt="image" src="https://user-images.githubusercontent.com/93315926/195972408-5c2ea88c-6a0c-4783-b4bc-23f6661d50fe.png">

## step 2: Download Selenium WebDriver framework

[Download link](https://www.selenium.dev/downloads/)

> I put the Path in /Users/linda/Documents/testproj

<img width="500" alt="image" src="https://user-images.githubusercontent.com/93315926/195972776-d46277b1-e2e7-4886-96dd-64e51535cc82.png">

## Step 3: Download Selenium Browser Driver

https://www.selenium.dev/documentation/webdriver/getting_started/install_drivers/

> I put the Path in /Users/linda/Documents/testproj/chromedriver

<img width="500" alt="image" src="https://user-images.githubusercontent.com/93315926/195973000-b4f80e2a-9d6a-49bb-825d-a9a4c6041a95.png">

> Choose the ChromeDriver version based on your chrome version!!

<img width="500" alt="image" src="https://user-images.githubusercontent.com/93315926/195973053-881c41f8-8f05-4d40-918b-51a6b101f47d.png">

> Choose the ChromeDriver version based on your Mac version!!

> If your processor is intel, choose chromedriver_mac64.zip
> If your processor is Apple M1, choose chromedriver_mac_arm64.zip

How to check processor: About this Mac <br>

<img width="500" alt="image" src="https://user-images.githubusercontent.com/93315926/195973326-54cc3c04-e8ee-4969-aebb-8875a57728e5.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/93315926/195973080-4ab48c30-cbe7-4e34-bbb4-dbdadac37873.png">

## Step 4: Install Java (JDK/JRE 1.8)
How to Install Java on MacOS?
https://www.geeksforgeeks.org/how-to-install-java-on-macos/

* How to set your java environment:

```java
$ /usr/libexec/java_home -V
```
/usr/local/Cellar/openjdk/18/libexec/openjdk.jdk/Contents/Home

```java
$ open -a ~/.bash_profile
```
Add:
export JAVA_HOME=/usr/local/Cellar/openjdk/18/libexec/openjdk.jdk/Contents/Home

```java
$ source ~/.bash_profile
```

```java
$ echo $JAVA_HOME
```

* How to check your java version:

```
$ java -version
$ javac -version
```

<img width="500" alt="image" src="https://user-images.githubusercontent.com/93315926/195971993-151c4ce0-343f-4c3a-b5e4-7c45ca12fbf0.png">

## Step 5:Create New Java Project using Visual studio Code

### Create New Java Project

* Open Command Pallete in VS Code (Ctrl / Cmd + Shift + P).
* Select: Java: Create Java Project…
* Select: No build tools
* Choose the project path, I choose /Users/linda/Documents/testproj
* Open project->Click App.java

<img width="200" alt="image" src="https://user-images.githubusercontent.com/93315926/195976169-9789c27d-8b40-43ca-9f02-46502608786d.png">

### Reference The Libraries

* Click on + button on the right of the “Referenced Libraries” row present inside the Java Projects column on the sidebar.

<img width="200" alt="image" src="https://user-images.githubusercontent.com/93315926/195976445-984dec6d-7f2a-4392-95d9-903de4ada042.png">

* Select all the .jar files you downloaded on the step 2 and insert.

<img width="200" alt="image" src="https://user-images.githubusercontent.com/93315926/195976241-480ea8de-2704-42c6-b132-fd0f4cc1a490.png">

If it looks like this, you’re good to go.

### Code & Run

create a new TestSelenium class:

```java
import org.openqa.selenium.By;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;

public class TestSelenium {
    public static void main(String[] args) throws InterruptedException {
        System.setProperty("webdriver.chrome.driver", "/Users/linda/Documents/testproj/chromedriver");
        WebDriver driver = new ChromeDriver();
        Actions actions = new Actions(driver);

        driver.get("http://www.google.com");
        driver.manage().window().maximize();
        Thread.sleep(2000);
        driver.findElement(By.name("q")).sendKeys("SFBU");
        actions.sendKeys(Keys.ENTER).build().perform();
        Thread.sleep(2000);
        driver.navigate().to("https://sfbu.edu");
        Thread.sleep(2000);
        String expectedTitle = "SFBU | San Francisco Bay University | SFBU";
        String actualTitle = driver.getTitle();
        System.out.println("Current open web page title is " + actualTitle);
        if (actualTitle.contentEquals(expectedTitle)) {
            System.out.println("Test Passed!");
        } else {
            System.out.println("Test Failed");
        }
        driver.close();
        driver.quit();
    }
}

```

Go to Run and click on Run Without Debugging.

### Test Result

<img width="500" alt="image" src="https://user-images.githubusercontent.com/93315926/195975968-2012ee10-260a-4e9d-8749-168945c438d6.png">

### Runing Error

> “chromedriver” cannot be opened because the developer cannot be verified.

Solution:

Step 1: find the chromedriver path. My path is: /Users/linda/Documents/testproj/chromedriver

Step 2: Now you need to tell Mac OS to trust this binary by lifting the quarantine. Do this by the following terminal command:

```
xattr -d com.apple.quarantine com.apple.quarantine /Users/linda/Documents/testproj/chromedriver
```


## Reference

https://medium.com/@krsambhav/setting-up-selenium-using-java-on-vs-code-512fcb7d7279

https://funnelgarden.com/setup-selenium-with-java-on-visual-studio-code/





