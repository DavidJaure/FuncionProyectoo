# FuncionProyectoo

/*La función que se presentará calculará el monto total de todos los créditos solicitados por un usuario que se filtra por su cedula. 

 

Al ingresar la cedula del usuario se buscará dentro de los presupuestos asociados en la tabla Presupuesto, después de esto se consulta dentro de la tabla créditos para sumar el ‘MontoTotal’ de todos los créditos de los presupuestos consultados. Al realizar la consulta la función devuelve la suma total de los créditos que se ha solicitado, sino existen créditos la función devuelve cero (0). */

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
