-- Create a view so the physician with SSN 9201977 can only check the prescribed medications of their own patients

CREATE VIEW Physician9201977_Meds AS
SELECT Pres_Time as "time", Pat_SSN as "SSN", Med_Name, dosage FROM prescribedfor
WHERE Phys_SSN = 9201977

-- Create a view that shows the pharmaceutical companies that have more than one contract with pharmacies with the following condition:
-- The length of the contract is less than 30 months.

CREATE VIEW PhaCo_cont_lt30mo AS
SELECT longtermcontract.PhC_Name As name, pharmaceuticalcompany.address, COUNT(longtermcontract.Pha_Address) As nr_contract	from pharmaceuticalcompany 
JOIN longtermcontract ON (pharmaceuticalcompany.name = longtermcontract.PhC_Name)
WHERE TIMESTAMPDIFF(MONTH,longtermcontract.start, longtermcontract.end) < 30
GROUP by longtermcontract.PhC_Name
HAVING COUNT(longtermcontract.Pha_Address) > 1;
