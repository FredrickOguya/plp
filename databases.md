
--creating the hospital_db database--

CREATE DATABASE `hospital_db`;

--selecting using the USE keyword--

USE `hospital_db`;

--creating patients table--

CREATE TABLE `patients` (
  `patient_id` INT NULL AUTO_INCREMENT,
  `first_name` VARCHAR(50) NOT NULL,
  `last_name` VARCHAR(45) NULL,
  `date_of_birth` DATE NULL,
  `gender` VARCHAR(1) NULL,
  `language` VARCHAR(50) NULL,
  PRIMARY KEY (`patient_id`),
  UNIQUE INDEX `patient_id_UNIQUE` (`patient_id` ASC) VISIBLE);


  --creating providers table--

  CREATE TABLE `providers` (
  `provider_id` INT NOT NULL AUTO_INCREMENT,
  `first_name` VARCHAR(45) NOT NULL,
  `last_name` VARCHAR(45) NOT NULL,
  `provider_speciality` VARCHAR(100) NULL,
  `email_address` VARCHAR(100) NULL,
  `phone_number` VARCHAR(45) NULL,
  `date_joined` DATE NULL,
  PRIMARY KEY (`provider_id`));

  --creating visits table--

  CREATE TABLE `visits` (
  `visit_id` INT NOT NULL AUTO_INCREMENT,
  `date_of_visit` DATE NOT NULL,
  `date_scheduled` DATE NOT NULL,
  `visit_department_id` INT NOT NULL,
  `visit_type` VARCHAR(45) NOT NULL,
  `blood_pressure_systollic` DECIMAL(20) NULL,
  `blood_pressure_diastollic` DECIMAL(20) NULL,
  `pulse` DECIMAL(10) NULL,
  `visit_status` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`visit_id`),
  FOREIGN KEY (`patient_id`) REFERENCE `patients` (`patient_id`),
  FOREIGN KEY (`provider_id`) REFERENCE `providers` (`provider_id`),
  UNIQUE INDEX `patient_id_UNIQUE` (`patient_id` ASC) VISIBLE);

  --creating ed_visits table--

  CREATE TABLE `ed_visits_table` (
  `ed_visits_id` INT NOT NULL AUTO_INCREMENT,
  `acuity` INT NOT NULL,
  `reason_for_visit` VARCHAR(45) NOT NULL,
  `disposition` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`ed_visits_id`),
  FOREIGN KEY (`patient_id`) REFERENCE `patients` (`patient_id`),
  FOREIGN KEY (`visit_id`) REFERENCE `visits` (`visit_id`),
  );

  -- creating admission table --

  CREATE TABLE `admissions` (
  `admission_id` INT NOT NULL AUTO_INCREMENT,
  `admission_date` DATE NOT NULL,
  `discharge_date` DATE NOT NULL,
  `service` VARCHAR(45) NOT NULL,
  `primary_diagnosis` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`admission_id`),
  FOREIGN KEY (`patient_id`) REFERENCE `patients` (`patient_id`),
  );

--creating discharges table--

  CREATE TABLE `discharges_table` (
  `discharge_date` DATE NOT NULL,
  `discharge_deposition` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`discharge_id`),
  FOREIGN KEY (`patient_id`) REFERENCE `patients` (`patient_id`),
  FOREIGN KEY (`admission_id`) REFERENCE `admission` (`admission_id`),
  );

