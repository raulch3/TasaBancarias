# TasaBancarias
---
### Base datos - Análisis de tasa bancarias en Panamá
-  La importancia de poder conocer los tasa de interés en el mercado en conceptos de Ahorros y Créditos, es importante para los sujetos de créditos y ahorradores ya que nos facilita o nos dan mas opciones a la hora de toma de decisiones
- Consulta de Tasa de interes promedios de ahorros y créditos, SPREAD como indentificador de mayor ganancia y menor ganancia desde los 8 hasta los 4.
- Ejemplo de consulta:
  ´´´´
  select
	b.nombre as Banco,
	b.tipo as TipoInsitucion,
	avg(CASE WHEN p.categoria = 'Activo'
		THEN h.tasa_porcentaje END) as 'tasa_activa_promedio',
	AVG(CASE WHEN p.categoria='Pasivo'
		THEN h.tasa_porcentaje END) as 'tasa_pasiva_promedio',
		AVG(CASE WHEN p.categoria='Activo'
		THEN h.tasa_porcentaje END)  -
		AVG(CASE WHEN p.categoria='Pasivo'
		THEN h.tasa_porcentaje END) as 'spread_pp'
		from 
HistoricoTasas h
INNER JOIN Bancos b on h.id_banco=b.id_banco
INNER JOIN TipoProducto p on h.id_producto=p.id_producto
group by b.nombre,b.tipo
´´´´
- VISTO DESDE SSM22
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/c093a6ed-6130-420f-b6e1-de0bf7bd0516" />
