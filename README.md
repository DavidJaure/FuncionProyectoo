# FuncionProyectoo
DELIMITER //

CREATE FUNCTION TotalCreditos(cedula INT)
RETURNS DECIMAL(10, 2)
DETERMINISTIC
BEGIN
    DECLARE Total DECIMAL(10, 2);

    
    SELECT SUM(MontoTotal) INTO Total
    FROM Creditos
    WHERE idPresupuesto IN (SELECT idPresupuesto FROM Presupuesto WHERE Cedula = cedula);

   
    RETURN Total;
END //

DELIMITER ;
