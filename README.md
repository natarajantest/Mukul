//17-04-2019 (openEmr assignment)
package initialize;

import java.time.Duration;
import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.edge.EdgeDriver;
import org.openqa.selenium.ie.InternetExplorerDriver;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.Select;

public class OpenEmr {
	public static void main(String[] args) throws InterruptedException
	{
		WebDriver driver = new EdgeDriver();
		System.setProperty("webdriver.edge.driver","SeleniumBasics2/MicrosoftWebDriver.exe");
		driver.manage().window().maximize();
		driver.manage().timeouts().implicitlyWait(20, TimeUnit.SECONDS);
		driver.get(" https://demo.openemr.io/d/openemr");
		driver.findElement(By.id("authUser")).sendKeys("admin");
		driver.findElement(By.id("clearPass")).sendKeys("pass");
		/*Select sc = new Select(driver.findElement(By.name("languageChoice")));
		sc.selectByValue("18");*/
		driver.findElement(By.className("fa-sign-in")).click();
		Actions act  = new Actions(driver);
		act.moveToElement(driver.findElement(By.xpath("//div[text()='Patient/Client']"))).build().perform();
		 act
			.keyDown(Keys.CONTROL)
			.pause(Duration.ofSeconds(1))
			.build()
			.perform();
		driver.findElement(By.xpath("//div[text()='New/Search']")).click();
		driver.switchTo().frame(driver.findElement(By.name("pat")));
		Thread.sleep(1000);
		driver.findElement(By.name("form_fname")).sendKeys("Baburao");
		driver.findElement(By.name("form_lname")).sendKeys("Apte");
		driver.findElement(By.id("form_DOB")).click();
		act.moveToElement(driver.findElement(By.xpath("//div[text()='17']"))).build().perform();
		driver.findElement(By.xpath("//div[text()='17']")).click();
		Select sc1 = new Select(driver.findElement(By.id("form_sex")));
		sc1.selectByValue("Male");
		driver.findElement(By.id("create")).click();
		driver.switchTo().defaultContent();
		driver.switchTo().frame(driver.findElement(By.id("modalframe")));
		driver.findElement(By.xpath("//input[@value='Confirm Create New Patient']")).click();
		 Thread.sleep(3000);
	    driver.switchTo().alert().accept();
	    driver.findElement(By.xpath("//div[@class='closeDlgIframe']")).click();
	     // driver.switchTo().frame(driver.findElement(By.name("timeout")));
	     // Actions act1=new Actions(driver);
	     act.moveToElement(driver.findElement(By.xpath("//div[@class='menuSection userSection']"))).build().perform();
	      driver.findElement(By.xpath("//ul//li[text()='Logout']")).click();
	    
		
	}

}

////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
(spicejet assignment)

package initialize;

import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.By.ById;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.edge.EdgeDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.Select;

public class SpiceJet {

	public static void main(String[] args) throws InterruptedException {
		// TODO Auto-generated method stub
		WebDriver driver = new EdgeDriver();
		driver.manage().window().maximize();
		driver.manage().timeouts().implicitlyWait(30, TimeUnit.SECONDS);
		driver.get("https://www.spicejet.com");


	driver.findElement(By.id("ctl00_mainContent_ddl_originStation1_CTXTaction")).click();
	driver.findElement(By.linkText("Mumbai (BOM)")).click();
	Thread.sleep(3000);
	driver.findElement(By.id("ctl00_mainContent_ddl_destinationStation1_CTXTaction")).click();
	driver.findElement(By.linkText("Delhi (DEL)")).click();
	Thread.sleep(3000);

	Actions act = new Actions(driver);
	act.moveToElement(driver.findElement(By.linkText("19"))).build().perform();
	driver.findElement(By.linkText("19")).click();
	Thread.sleep(3000);

//	act.moveToElement(driver.findElement(By.linkText("25"))).build().perform();
//	driver.findElement(By.linkText("25")).click();
	
	driver.findElement(By.className("paxinfo")).click();
    for(int i=0;i<=3;i++)
    {  
	driver.findElement(By.id("hrefIncAdt")).click();
	i=i+1;
    }	
    Thread.sleep(3000);
    driver.findElement(By.id("btnclosepaxoption")).click();
    
   Select sc=new Select(driver.findElement(By.id("ctl00_mainContent_DropDownListCurrency")));
   sc.selectByValue("AED");
   Thread.sleep(3000);
   driver.findElement(By.id("ctl00_mainContent_btn_FindFlights")).click();
   
	}

}
