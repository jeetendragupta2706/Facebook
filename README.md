# Facebook
Scenario to send message to the person using chat using webdriver for Facebook Application


import java.util.concurrent.TimeUnit;
import org.openqa.selenium.By;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.ie.InternetExplorerDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;
public class Facebook_chat {
	public static void main(String[] args) {
		WebDriver driver = new InternetExplorerDriver();
		driver.manage().deleteAllCookies();
		driver.manage().timeouts().implicitlyWait(20, TimeUnit.SECONDS);
		driver.navigate().to("https://www.facebook.com/");
		WebDriverWait  waitdriver = new WebDriverWait(driver,30);
		waitdriver.until(ExpectedConditions.visibilityOfElementLocated(By.id("u_0_e")));
		driver.findElement(By.id("email")).sendKeys("EmailID");
		driver.findElement(By.id("pass")).sendKeys("Password");
		// Click on Login Button 
		driver.findElement(By.id("u_0_l")).click();
		waitdriver.until(ExpectedConditions.visibilityOfElementLocated(By.className("_2s25")));
		System.out.println("Login to facebook Successfull");
		driver.manage().timeouts().implicitlyWait(30, TimeUnit.SECONDS);		
		
		// Function to say hi in the chat 	
		By Chat_search =By.className("_58al");			
		driver.findElement(Chat_search).sendKeys("Name of person whom you want to send chat");
		waitdriver.until(ExpectedConditions.visibilityOfElementLocated(By.className("_364g")));		
		driver.findElement(By.className("_364g")).click();
		System.out.println("Chat Window Open Successfully");
		waitdriver.until(ExpectedConditions.visibilityOfElementLocated(By.xpath("//a[@data-tooltip-content='Krishna Shah']")));		
		String ChatPersonName = driver.findElement(By.xpath("//a[@data-tooltip-content='Name of person whom you want to send chat']")).getText();		
		if(ChatPersonName.contentEquals("Name of person whom you want to send chat"))
		{
			System.out.println("Now Writing Chat message for the Person");
			driver.findElement(By.xpath("//div[@class='_5rpu']")).clear();
			driver.findElement(By.xpath("//div[@class='_5rpu']")).sendKeys(new String[] {"Hi I am chattting with you using selenium code"});					
			driver.findElement(By.xpath("//div[@class='_5rpu']")).sendKeys(Keys.ENTER);
			System.out.println("Chat Successfully Send to the person");
		}
		else
		{
			System.out.println("Unable to Place chat with Person");
		}		
	}
}


