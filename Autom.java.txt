
import org.junit.Test;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.edge.EdgeDriver;
import org.openqa.selenium.interactions.Actions;
import org.junit.Assert;


public class autom {
    By model = By.xpath("//input[@id='brandTooltipBrandAutocompleteInput-model']");
    By region = By.xpath("//input[@id='brandTooltipBrandAutocompleteInput-region']");
    By brand = By.xpath("//input[@id='brandTooltipBrandAutocompleteInput-brand']");
    By yearFrom = By.xpath("//select[@id='yearFrom']");
    By yearTo = By.xpath("//select[@id='yearTo']");
    By priceFrom = By.xpath("//input[@name='price_ot']");
    By priceTo = By.xpath("//input[@name='price_do']");
    By submitElement = By.xpath("//button[@type='submit']");


    @Test
    public void openSite() throws InterruptedException {
        System.setProperty("webdriver.chrome.driver", "src/main/resources/chromedriver.exe");
        WebDriver driver = new ChromeDriver();
        driver.get("https://auto.ria.com/");


       driver.findElement(brand).sendKeys("Ford");
      Thread.sleep(4000);
      driver.findElement(By.xpath("//a[@data-value='24']")).click();

        driver.findElement(model).sendKeys("Edge");
        Thread.sleep(3000);
        driver.findElement(By.xpath("//a[@data-value='1945']")).click();

       driver.findElement(region).sendKeys("Харьков");
    Thread.sleep(3000);
     driver.findElement(By.xpath("//*[@id='brandTooltipBrandAutocomplete-region']/ul/li[1]/a")).click();

        driver.findElement(yearFrom).sendKeys("2019");
        Thread.sleep(3000);
        driver.findElement(By.xpath("//*[@id='yearFrom']/option[5]")).click();

        driver.findElement(yearTo).sendKeys("2022");
        driver.findElement(By.xpath("//*[@id='yearTo']/option[2]")).click();

        driver.findElement(priceFrom).sendKeys("2900");
        driver.findElement(By.xpath("//*[@id='priceFrom']")).click();

        driver.findElement(priceTo).sendKeys("20190000");
        driver.findElement(By.xpath("//*[@id='priceTo']")).click();

        driver.findElement(submitElement).click();
        Thread.sleep(3000);

        Assert.assertEquals("https://auto.ria.com/search/?categories.main.id=1&price.currency=1&price.USD.gte=2900&price.USD.lte=20190000&indexName=auto,order_auto,newauto_search&region.id[0]=7&city.id[0]=7&brand.id[0]=24&model.id[0]=1945&year[0].gte=2019&year[0].lte=2022&size=20", driver.getCurrentUrl());

        


    }
}