# TesteAutomacao
 exercicios de automação
 
//PomProject

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
<modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>cursosellenium</artifactId>
    <version>1.0-SNAPSHOT</version>
    <dependencies>

        <dependency>
            <groupId>commons-io</groupId>
            <artifactId>commons-io</artifactId>
            <version>2.16.1</version>
        </dependency>



        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-java</artifactId>
            <version>4.19.1</version>
        </dependency>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.13.2</version>
        </dependency>
    </dependencies>


    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>

</project>

-------------------------------------------------------------------------------
//CadastroCliente

package org.Keeggo;
import org.junit.Assert;
import org.junit.Test;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;



public class CadastroCliente {


    @Test
    public  void teste() {

        WebDriver driver = new ChromeDriver();
        driver.get("file:///C:/Users/lucas/AppData/Local/Temp/6360215f-4b96-45ae-844e-25f2a06fd2c9_demoBank.zip.2c9/demoBank/WEB_BANK_CAD_CLI.html"); // para colocar a URL da site que voce quer
        driver.findElement(By.id("txtNome")).sendKeys("Lucas Giovanelli");
        driver.findElement(By.id("txtCPF")).sendKeys("41136289862");
        driver.findElement(By.id("txtRG")).sendKeys("53056518-3");
        driver.findElement(By.id("txtIdade")).sendKeys("23");
        driver.findElement(By.xpath("//button[.='Salvar']")).click();
        Assert.assertEquals("Cadastro efetuado com sucesso","Cadastro efetuado com sucesso");
    }

}



-------------------------------------------------------------------------------

//Login

package org.Keeggo;

import org.junit.Assert;
import org.junit.Test;
import org.openqa.selenium.By;
import org.openqa.selenium.OutputType;
import org.openqa.selenium.TakesScreenshot;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.apache.commons.io.FileUtils;
import java.io.File;
import java.io.IOException;

public class login {

    @Test
    public void teste() throws IOException {
        WebDriver driver = new ChromeDriver();
        driver.get("file:///C:/Users/lucas/AppData/Local/Temp/bb193f71-7fe4-4876-9c6a-04ba2a1c3d9e_demoBank.zip.d9e/demoBank/WEB_BANK_LOGIN.html"); // para colocar a URL da site que voce quer
        driver.findElement(By.id("txtusuario")).sendKeys("Lucas@Giovanelli");
        driver.findElement(By.id("txtsenha")).sendKeys("123456");
        driver.findElement(By.xpath("//button[.='Login']")).click();
        File scrFile = ((TakesScreenshot)driver).getScreenshotAs(OutputType.FILE);
        FileUtils.copyFile(scrFile, new File("C:\\Users\\lucas\\OneDrive\\Desktop\\prints"));
        Assert.assertEquals("Login feito","Login invalido");  //comparação dos resultdos da pagina se "login feito" passed se "login invalido" failed
    }

    @Test
    public void testeUsuarioInvalido() throws IOException {
        WebDriver driver = new ChromeDriver();
        driver.get("file:///C:/Users/lucas/AppData/Local/Temp/bb193f71-7fe4-4876-9c6a-04ba2a1c3d9e_demoBank.zip.d9e/demoBank/WEB_BANK_LOGIN.html");
        driver.findElement(By.id("txtusuario")).sendKeys("UsuarioInvalido");
        driver.findElement(By.id("txtsenha")).sendKeys("123456");
        driver.findElement(By.xpath("//button[.='Login']")).click();
        File scrFile = ((TakesScreenshot)driver).getScreenshotAs(OutputType.FILE);
        FileUtils.copyFile(scrFile, new File("C:\\Users\\lucas\\OneDrive\\Desktop\\prints"));
        Assert.assertEquals("Login invalido","Login feito");
    }

    @Test
    public void testeSenhaInvalida() throws IOException {
        WebDriver driver = new ChromeDriver();
        driver.get("file:///C:/Users/lucas/AppData/Local/Temp/bb193f71-7fe4-4876-9c6a-04ba2a1c3d9e_demoBank.zip.d9e/demoBank/WEB_BANK_LOGIN.html");
        driver.findElement(By.id("txtusuario")).sendKeys("Lucas@Giovanelli");
        driver.findElement(By.id("txtsenha")).sendKeys("SenhaInvalida");
        driver.findElement(By.xpath("//button[.='Login']")).click();
        File scrFile = ((TakesScreenshot)driver).getScreenshotAs(OutputType.FILE);
        FileUtils.copyFile(scrFile, new File("C:\\Users\\lucas\\OneDrive\\Desktop\\prints"));
        Assert.assertEquals("Login invalido","Login feito");
    }

}


---------------------------------------------------------------------------------------------
//Webbank

import org.junit.Assert;
import org.junit.Test;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class WebBank {

    @Test

    public void teste() {
        WebDriver driver = new ChromeDriver();
        driver.get("file:///C:/Users/lucas/AppData/Local/Temp/3d1252fd-2888-4ca5-9e82-e3ede11ed7cd_demoBank.zip.7cd/demoBank/WEB_BANK.html");
        driver.findElement(By.id("txtvalor")).sendKeys("100");
        driver.findElement(By.id("txtConta")).sendKeys("0110");
        driver.findElement(By.id("txtDigito")).sendKeys("7");
        driver.findElement(By.id("txtDescr")).sendKeys("pix do pão");
        driver.findElement(By.xpath("//button[.='Tranferir']")).click();
    }


    @Test
    public void testeTransferenciaValorInvalido() {
        WebDriver driver = new ChromeDriver();
        driver.get("file:///C:/Users/lucas/AppData/Local/Temp/3d1252fd-2888-4ca5-9e82-e3ede11ed7cd_demoBank.zip.7cd/demoBank/WEB_BANK.html");
        driver.findElement(By.id("txtvalor")).sendKeys("-100");
        driver.findElement(By.id("txtConta")).sendKeys("0110");
        driver.findElement(By.id("txtDigito")).sendKeys("7");
        driver.findElement(By.id("txtDescr")).sendKeys("pix do pão");
        driver.findElement(By.xpath("//button[.='Tranferir']")).click();}


    @Test
    public void testeTransferenciaSemDescricao() {
        WebDriver driver = new ChromeDriver();
        driver.get("file:///C:/Users/lucas/AppData/Local/Temp/3d1252fd-2888-4ca5-9e82-e3ede11ed7cd_demoBank.zip.7cd/demoBank/WEB_BANK.html");
        driver.findElement(By.id("txtvalor")).sendKeys("100");
        driver.findElement(By.id("txtConta")).sendKeys("0110");
        driver.findElement(By.id("txtDigito")).sendKeys("7");
        driver.findElement(By.xpath("//button[.='Tranferir']")).click();}





}

