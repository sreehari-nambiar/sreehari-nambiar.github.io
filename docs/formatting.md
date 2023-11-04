# Formatting

(section-label1)=
## STRING:

    To change format of a number or date column,
      -  first convert it to a string
      -  then alter using a mask
    
    Oracle's built-in function: TO_CHAR(column OR value, <'FORMAT Mask>)
    
    Example:
    SELECT invoice_id,
           invoice_date,
           TO_CHAR(invoice_date, 'MON-DD-YYYY') AS varchar_date,
           invoice_total,
           TO_CHAR(invoice_total, '$999,999.99) AS varchar_total
    FROM   invoices;

Common STRING Functions:

    LTRIM(string[, trim_string]) - removes any spaces from left, if trim_string is specified, removes all trim_string characters 
    RTRIM(string[, trim_string])
    TRIM([trim_char FROM] string) - removes spaces from left and right, if trim_car is specified, removes trim_char from both sides
    LPAD(string, length[, pad_string])
    RPAD(string, length[, pad_string])
    LOWER(string)
    UPPER(string)
    INITCAP(string)

    Example:
    SELECT  LTRIM('   John Smith   ') AS ltrim1,
            RTRIM('   John Smith   ') AS rtrim1,
            TRIM('   John Smith   ')  AS trim1,
            LTRIM('$0019.99', '$0')   AS ltrim2,
            TRIM('$' FROM '$0019.99') AS trim2,
            LPAD('$19.99', 15)        AS lpad1,
            LPAD('$2150.78', 15)      AS lpad2,
            LPAD('$2150.78', 15, '.') AS lpad3,
            RPAD('John', 15)          AS rpad1,
            RPAD('John', 15, '.')     AS rpad2,
            LOWER('LOWER')            AS lower1,
            UPPER('upper')            AS upper1,
            INITCAP('john smith')     AS initcap1,
            INITCAP('STEVE SMITH')    AS initcap2
    FROM    dual;
            
    
(section-label2)=    
## NUMBER

    If numerica data is stored as CHAR, data will not sort numerically or allow for arithmetic.

    Example:
    SELECT *
    FROM    string_sample
    ORDER BY TO_NUMBER(id);

Common NUMERIC Functions:

| Functions                      | Descrption                                                                                     |
| ------------------------------ | ---------------------------------------------------------------------------------------------- |
| ROUND(number[, length])        | Returns "number" rounded to the precision specified by "length".                               |
|                                | If "lenghh" is positive, digits to the right of decimal are rounded.                           |
|                                | If "length" is negative, digits to the left of decimal are rounded.                            |
| TRUNC(number[. length])        | Returns "number" truncated as specified by "length"                                            |
|                                | If "length" is omitted, it truncates all numbers to the right if decimal.                      |
|                                | If "length" is negative, it truncates specified number of digits to the left of decimal point. |
| CEIL(number)                   | Returns the smallest integer greater than or equal to "number".                                |
| FLOOR(number)                  | Returns the largest integer less than or equal to "number".                                    |
| ABS(number)                    | Returns the absolute value of the "number".                                                    |
| SIGN(number)                   | Retuens -1 if "number" < 0, 0 if "number" = 0, 1 if "number" > 0.                              |
| MOD(number, number_divisor)    | Returns the remainder after "number" is divided by "number_divisor".                           |
| POWER(number, number_exponent) | Returns the "number" after it is raised to the power of "number_exponent".                     |
| SQRT(number)                   | Returns the square root of the "number".                                                       |
    

    Example:
    <img width="389" alt="image" src="https://github.com/sreehari-nambiar/sql/assets/23268641/22b9f2e3-6e56-402d-be89-082ea76dbf50">

(section-label3)=
## DATE & TIME:

    * In Oracle, TIME is automatically stored with DATE datatype.
    * If not specified, TIME is set to 12.00 AM by default which is the first second of any day.
    * You cannot see TIME when you select a DATE column unless you covert it to text and mask to show Hours, Mins, Seconds.

    Example:
    SELECT sysdate as todays_date,
           TO_CHAR(sysdate, 'DD-MON-YYYY HH24:MI:SS') as today_date_time
    FROM   dual;
    
    Tip – Remember that if you use the = operator to look for specific dates, it only returns dates with 12:00am as the time.  If you have times                stored, you’re better off using range operators like >= or <= .
    

### Common DATE Functions:

    <img width="396" alt="image" src="https://github.com/sreehari-nambiar/sql/assets/23268641/9ee368fe-f791-4117-868e-c607052f04bd">

    Example:
    <img width="396" alt="image" src="https://github.com/sreehari-nambiar/sql/assets/23268641/b22f5928-371c-4e72-920f-ff4ac4f5d0b1">
