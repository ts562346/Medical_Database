-- Create a stored procedure that shows all prescribed medications (names, dosages and times) issued by a physician
-- to a patient ordered by dosage in Ascending order.

-- The stored procedure should take the patient's name and the physician's name as input.

delimiter //
CREATE PROCEDURE GET_PRESCRIBED_MEDICINES(
	IN patient_name varchar(45),
    IN physician_name varchar(45)    
)
BEGIN
	DECLARE patient_SSN INT(11);
	DECLARE physician_SSN INT(11);
	SELECT  SSN INTO patient_SSN FROM person WHERE person.name = patient_name;
	SELECT  SSN INTO physician_SSN FROM person WHERE person.name = physician_name;
	SELECT prescribedfor.Med_Name, prescribedfor.dosage, prescribedfor.Pres_Time AS time from prescribedfor
	WHERE prescribedfor.Pat_SSN = patient_SSN and prescribedfor.Phys_SSN = physician_SSN;
END;//

CALL GET_PRESCRIBED_MEDICINES('Tiera Hook', 'Minta Cook');

-- Write a stored procedure that creates a new prescription or adds more medicines to an existing prescription. 

delimiter //
create procedure CREATE_PRESCRIPTION_WITH_MEDICINE(
    IN paitent_SSN INT(11),
    IN physician_SSN INT(11),
    IN medicine VARCHAR(50),
    IN dose decimal(10, 2),
    IN new_pres bool,
    IN pres_time datetime
)
BEGIN
	IF (new_pres) THEN
		INSERT INTO prescription VALUE(pres_time, physician_SSN, paitent_SSN);
        INSERT INTO prescribedfor VALUE(pres_time, physician_SSN, paitent_SSN, medicine, dose);
    ELSE 
		INSERT INTO prescribedfor VALUE(pres_time, physician_SSN, paitent_SSN, medicine, dose);
	END IF;
END;//

CALL CREATE_PRESCRIPTION_WITH_MEDICINE('1643883', '9201977', 'Angiomax', 0.15, '1', '2020-03-15 00:30:01' );
CALL CREATE_PRESCRIPTION_WITH_MEDICINE('1643883', '9201977', 'Benazepril', 2.75, '0', '2020-03-15 00:30:01' );

SELECT * FROM prescribedfor where Phys_SSN = '9201977' and Pat_SSN = '1643883';
