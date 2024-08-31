--creating patients table--

CREATE TABLE `hospital_db`.`patients` (
  `patient_id` INT NULL AUTO_INCREMENT,
  `first_name` VARCHAR(50) NOT NULL,
  `last_name` VARCHAR(45) NULL,
  `date_of_birth` DATE NULL,
  `gender` VARCHAR(1) NULL,
  `language` VARCHAR(50) NULL,
  PRIMARY KEY (`patient_id`),
  UNIQUE INDEX `patient_id_UNIQUE` (`patient_id` ASC) VISIBLE);

  --creating providers table--

  CREATE TABLE `hospital_db`.`providers` (
  `provider_id` INT NOT NULL AUTO_INCREMENT,
  `first_name` VARCHAR(45) NOT NULL,
  `last_name` VARCHAR(45) NOT NULL,
  `provider_speciality` VARCHAR(100) NULL,
  `email_address` VARCHAR(100) NULL,
  `phone_number` VARCHAR(45) NULL,
  `date_joined` DATE NULL,
  PRIMARY KEY (`provider_id`));

  --creating visits table--

  CREATE TABLE `hospital_db`.`visits` (
  `visit_id` INT NOT NULL AUTO_INCREMENT,
  `patient_id` VARCHAR(45) NULL,
  `provider_id` INT NULL,
  `date_of_visit` DATE NOT NULL,
  `date_scheduled` DATE NOT NULL,
  `visit_department_id` INT NOT NULL,
  `visit_type` VARCHAR(45) NOT NULL,
  `blood_pressure_systollic` DECIMAL(20) NULL,
  `blood_pressure_diastollic` DECIMAL(20) NULL,
  `pulse` DECIMAL(10) NULL,
  `visit_status` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`visit_id`),
  UNIQUE INDEX `patient_id_UNIQUE` (`patient_id` ASC) VISIBLE);

  --creating visits table--

  CREATE TABLE `hospital_db`.`ed_visits_table` (
  `ed_visits_id` INT NOT NULL AUTO_INCREMENT,
  `visit_id` INT NULL,
  `patient_id` INT NULL,
  `acuity` INT NOT NULL,
  `reason_for_visit` VARCHAR(45) NOT NULL,
  `disposition` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`ed_visits_id`));

  -- creating admission table --

  CREATE TABLE `hospital_db`.`admissions` (
  `admission_id` INT NOT NULL AUTO_INCREMENT,
  `patient_id` INT NULL,
  `admission_date` DATE NOT NULL,
  `discharge_date` DATE NOT NULL,
  `service` VARCHAR(45) NOT NULL,
  `primary_diagnosis` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`admission_id`));

--creating discharges table--

  CREATE TABLE `hospital_db`.`discharges_table` (
  `admisiion_id` INT 
  `patient_id` INT ,
  `discharge_date` DATE NOT NULL,
  `discharge_deposition` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`discharge_id`));

