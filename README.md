# demostore.x-cart
Automated tests for demostore.x-cart.com

package register;

import java.util.concurrent.TimeUnit;
import org.junit.*;
import static org.junit.Assert.*;
import org.openqa.selenium.*;
import org.openqa.selenium.firefox.FirefoxDriver;

public class Reg {
  private WebDriver driver;
  private String baseUrl;
  private StringBuffer verificationErrors = new StringBuffer();

  @Before
  public void setUp() throws Exception {
    driver = new FirefoxDriver();
    baseUrl = "https://demostore.x-cart.com/";
    driver.manage().timeouts().implicitlyWait(30, TimeUnit.SECONDS);
  }

  @Test
  public void testUntitled() throws Exception {
	for (int i = 0; i < 10; i++) {
	String s = Integer.toString(i);
    driver.get(baseUrl + "/");
    driver.findElement(By.xpath("(//button[@type='button'])[2]")).click();
    driver.findElement(By.cssSelector("a.popup-button.create-account-link")).click();
    driver.findElement(By.id("login")).clear();
    driver.findElement(By.id("login")).sendKeys("test2"+s+"@gmail.com");
    driver.findElement(By.id("password")).clear();
    driver.findElement(By.id("password")).sendKeys("1234");
    driver.findElement(By.id("password-conf")).clear();
    driver.findElement(By.id("password-conf")).sendKeys("1234");
    driver.findElement(By.xpath("(//button[@type='submit'])[7]")).click();
    driver.findElement(By.cssSelector("div.dropdown.header_bar-my_account > a")).click();
    driver.findElement(By.cssSelector("ul.account-links.dropdown-menu > li.account-link-logoff > a.log-off.icon-logout > span")).click();
  }
  }

	
  @After
  public void tearDown() throws Exception {
    driver.quit();
    String verificationErrorString = verificationErrors.toString();
    if (!"".equals(verificationErrorString)) {
      fail(verificationErrorString);
    }
  }
}
