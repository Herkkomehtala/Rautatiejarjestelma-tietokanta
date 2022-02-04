# SQL-skripti

Tämän scriptin suorittamalla voit luoda tämän harjoitustyön tietokannan kokonaisuudessaan mihin tahansa tyhjään mariaDB-tietokantaan kokeillaksesi sitä: 

```
-- MySQL Workbench Forward Engineering

SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0;
SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0;
SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION';

-- -----------------------------------------------------
-- Schema rautatiejarjestelma_db
-- -----------------------------------------------------

-- -----------------------------------------------------
-- Schema rautatiejarjestelma_db
-- -----------------------------------------------------
CREATE SCHEMA IF NOT EXISTS `rautatiejarjestelma_db` DEFAULT CHARACTER SET utf8 ;
USE `rautatiejarjestelma_db` ;

-- -----------------------------------------------------
-- Table `rautatiejarjestelma_db`.`Person`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `rautatiejarjestelma_db`.`Person` (
  `PersonID` INT NOT NULL,
  `Firstname` VARCHAR(45) NOT NULL,
  `Lastname` VARCHAR(45) NOT NULL,
  `Birthday` DATE NOT NULL,
  `TYPE` VARCHAR(45) NOT NULL,
  `Gender` CHAR(1) NOT NULL,
  PRIMARY KEY (`PersonID`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `rautatiejarjestelma_db`.`Receipt`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `rautatiejarjestelma_db`.`Receipt` (
  `ReceiptID` INT NOT NULL,
  `Seat` VARCHAR(45) NOT NULL,
  `Price` INT NOT NULL,
  `Person_PersonID` INT NOT NULL,
  PRIMARY KEY (`ReceiptID`),
  INDEX `fk_Receipt_Person1_idx` (`Person_PersonID` ASC),
  CONSTRAINT `fk_Receipt_Person1`
    FOREIGN KEY (`Person_PersonID`)
    REFERENCES `rautatiejarjestelma_db`.`Person` (`PersonID`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `rautatiejarjestelma_db`.`Company`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `rautatiejarjestelma_db`.`Company` (
  `CompanyID` INT NOT NULL,
  `CEO` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`CompanyID`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `rautatiejarjestelma_db`.`Train`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `rautatiejarjestelma_db`.`Train` (
  `TrainID` INT NOT NULL,
  `Manufacturer` VARCHAR(45) NOT NULL,
  `SeatAmount` INT NOT NULL,
  `Horsepower` INT NOT NULL,
  `Company_CompanyID` INT NOT NULL,
  PRIMARY KEY (`TrainID`),
  INDEX `fk_Train_Company1_idx` (`Company_CompanyID` ASC),
  CONSTRAINT `fk_Train_Company1`
    FOREIGN KEY (`Company_CompanyID`)
    REFERENCES `rautatiejarjestelma_db`.`Company` (`CompanyID`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `rautatiejarjestelma_db`.`Trip`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `rautatiejarjestelma_db`.`Trip` (
  `TripID` INT NOT NULL,
  `DepartingStation` VARCHAR(10) NOT NULL,
  `ArrivalStation` VARCHAR(10) NOT NULL,
  `EstimatedTime` TIME NOT NULL,
  `TotalDistance` INT NOT NULL,
  `Train_TrainID` INT NOT NULL,
  PRIMARY KEY (`TripID`),
  INDEX `fk_Trip_Train1_idx` (`Train_TrainID` ASC),
  CONSTRAINT `fk_Trip_Train1`
    FOREIGN KEY (`Train_TrainID`)
    REFERENCES `rautatiejarjestelma_db`.`Train` (`TrainID`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `rautatiejarjestelma_db`.`Freight`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `rautatiejarjestelma_db`.`Freight` (
  `FreightID` INT NOT NULL,
  `Category` VARCHAR(45) NOT NULL,
  `Type` VARCHAR(45) NOT NULL,
  `Amount` INT NOT NULL,
  `TotalWeight` INT NOT NULL,
  `Trip_TripID` INT NOT NULL,
  PRIMARY KEY (`FreightID`),
  INDEX `fk_Freight_Trip1_idx` (`Trip_TripID` ASC),
  CONSTRAINT `fk_Freight_Trip1`
    FOREIGN KEY (`Trip_TripID`)
    REFERENCES `rautatiejarjestelma_db`.`Trip` (`TripID`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `rautatiejarjestelma_db`.`Trip_has_Receipt`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `rautatiejarjestelma_db`.`Trip_has_Receipt` (
  `Trip_TripID` INT NOT NULL,
  `Receipt_ReceiptID` INT NOT NULL,
  PRIMARY KEY (`Trip_TripID`, `Receipt_ReceiptID`),
  INDEX `fk_Trip_has_Receipt_Receipt1_idx` (`Receipt_ReceiptID` ASC),
  INDEX `fk_Trip_has_Receipt_Trip_idx` (`Trip_TripID` ASC),
  CONSTRAINT `fk_Trip_has_Receipt_Trip`
    FOREIGN KEY (`Trip_TripID`)
    REFERENCES `rautatiejarjestelma_db`.`Trip` (`TripID`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_Trip_has_Receipt_Receipt1`
    FOREIGN KEY (`Receipt_ReceiptID`)
    REFERENCES `rautatiejarjestelma_db`.`Receipt` (`ReceiptID`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `rautatiejarjestelma_db`.`Staff`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `rautatiejarjestelma_db`.`Staff` (
  `Person_PersonID` INT NOT NULL,
  `Trip_TripID` INT NOT NULL,
  `Rank` VARCHAR(20) NOT NULL,
  `Salary` INT NOT NULL,
  PRIMARY KEY (`Person_PersonID`, `Trip_TripID`),
  INDEX `fk_Person_has_Trip_Trip1_idx` (`Trip_TripID` ASC),
  INDEX `fk_Person_has_Trip_Person1_idx` (`Person_PersonID` ASC),
  CONSTRAINT `fk_Person_has_Trip_Person1`
    FOREIGN KEY (`Person_PersonID`)
    REFERENCES `rautatiejarjestelma_db`.`Person` (`PersonID`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_Person_has_Trip_Trip1`
    FOREIGN KEY (`Trip_TripID`)
    REFERENCES `rautatiejarjestelma_db`.`Trip` (`TripID`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `rautatiejarjestelma_db`.`MaintenanceReport`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `rautatiejarjestelma_db`.`MaintenanceReport` (
  `MaintenanceID` INT NOT NULL,
  `Date` DATE NOT NULL,
  `Type` VARCHAR(20) NOT NULL,
  `Status` VARCHAR(20) NOT NULL,
  `Other` VARCHAR(45) NULL,
  `Train_TrainID` INT NOT NULL,
  PRIMARY KEY (`MaintenanceID`),
  INDEX `fk_MaintenanceReport_Train1_idx` (`Train_TrainID` ASC),
  CONSTRAINT `fk_MaintenanceReport_Train1`
    FOREIGN KEY (`Train_TrainID`)
    REFERENCES `rautatiejarjestelma_db`.`Train` (`TrainID`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;


SET SQL_MODE=@OLD_SQL_MODE;
SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS;
SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS;
```
