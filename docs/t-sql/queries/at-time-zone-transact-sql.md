---
title: AT TIME ZONE (Transact-SQL)
ms.date: 06/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.custom: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- AT TIME ZONE
- AT_TIME_ZONE_TSQL
helpviewer_keywords:
- AT TIME ZONE function
ms.assetid: 311f682f-7f1b-43b6-9ea0-24e36b64f73a
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current||=azure-sqldw-latest||>= sql-server-2016||>= sql-server-linux-2017||= sqlallproducts-allversions
ms.openlocfilehash: fa6c6e8fbee0d28e797a8d528b8eefb9b02a23ab
ms.sourcegitcommit: b8933ce09d0e631d1183a84d2c2ad3dfd0602180
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83152094"
---
# <a name="at-time-zone-transact-sql"></a>AT TIME ZONE (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

Convertit une valeur *inputdate* en valeur *datetimeoffset* correspondante dans le fuseau horaire cible. Quand la valeur *inputdate* est fournie sans informations sur le décalage, la fonction applique le décalage du fuseau horaire en supposant que la valeur *inputdate* figure dans le fuseau horaire cible. Si la valeur *inputdate* est fournie en tant que valeur *datetimeoffset*, la clause **AT TIME ZONE** la convertit dans le fuseau horaire cible selon les règles de conversion de fuseau horaire.  

L’implémentation **AT TIME ZONE** utilise un mécanisme Windows pour convertir les valeurs **datetime** sur plusieurs fuseaux horaires.  

![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>Syntaxe

```sql
inputdate AT TIME ZONE timezone  
```

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments

*inputdate*  
Expression qui peut être résolue en une valeur **smalldatetime**, **datetime**, **datetime2** ou **datetimeoffset**.  

*timezone* Nom du fuseau horaire de destination. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se base sur les fuseaux horaires qui sont stockés dans le Registre Windows. Les fuseaux horaires installés sur l’ordinateur sont stockés dans la ruche de Registre suivante : **KEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones**. Vous pouvez également consulter une liste des fuseaux horaires installés dans [sys.time_zone_info &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-time-zone-info-transact-sql.md).  

## <a name="return-types"></a>Types de retour

Retourne le type de données de **datetimeoffset**.

## <a name="return-value"></a>Valeur de retour

Valeur **datetimeoffset** dans le fuseau horaire cible.
  
## <a name="remarks"></a>Notes

**AT TIME ZONE** applique des règles spécifiques pour la conversion des valeurs d’entrée de types **smalldatetime**, **datetime** et **datetime2** qui se trouvent dans un intervalle de temps impacté par le passage à l’heure d’été (DST) :

- Quand l’horloge est avancée, il y a un écart avec l’heure locale égal à la durée de l’ajustement de l’horloge. Cette durée est généralement d’une heure, mais elle peut être de 30 ou 45 minutes selon le fuseau horaire. Les heures comprises dans cet intervalle sont converties avec le décalage *après* le passage à l’heure d’été.  

    ```sql
    /*  
        Moving to DST in "Central European Standard Time" zone: 
        offset changes from +01:00 -> +02:00   
        Change occurred on March 29th, 2015 at 02:00:00.   
        Adjusted local time became 2015-03-29 03:00:00.  
    */  

    --Time before DST change has standard time offset (+01:00)
    SELECT CONVERT(datetime2(0), '2015-03-29T01:01:00', 126)     
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-03-29 01:01:00 +01:00   
  
    /*
      Adjusted time from the "gap interval" (between 02:00 and 03:00)
      is moved 1 hour ahead and presented with the summer time offset
      (after the DST change) 
    */
    SELECT CONVERT(datetime2(0), '2015-03-29T02:01:00', 126)   
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-03-29 03:01:00 +02:00

    --Time after 03:00 is presented with the summer time offset (+02:00)
    SELECT CONVERT(datetime2(0), '2015-03-29T03:01:00', 126)   
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-03-29 03:01:00 +02:00  
  
    ```

- Quand l’horloge est reculée, deux heures de l’heure locale se chevauchent sur une heure.  Dans ce cas, les heures comprises dans cet intervalle avec chevauchement sont présentées avec le décalage *avant* l’ajustement de l’horloge :  
  
    ```sql
    /*  
        Moving back from DST to standard time in
        "Central European Standard Time" zone:
        offset changes from +02:00 -> +01:00.
        Change occurred on October 25th, 2015 at 03:00:00.
        Adjusted local time became 2015-10-25 02:00:00
    */  

    --Time before the change has DST offset (+02:00)
    SELECT CONVERT(datetime2(0), '2015-10-25T01:01:00', 126)
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-10-25 01:01:00 +02:00  

    /*
      Time from the "overlapped interval" is presented with standard time 
      offset (before the change)
    */
    SELECT CONVERT(datetime2(0), '2015-10-25T02:00:00', 126)
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-10-25 02:00:00 +02:00  


    --Time after 03:00 is regularly presented with the standard time offset (+01:00)
    SELECT CONVERT(datetime2(0), '2015-10-25T03:01:00', 126)
    AT TIME ZONE 'Central European Standard Time';
    --Result: 2015-10-25 03:01:00 +01:00
  
    ```

Étant donné que certaines informations (comme les règles de fuseau horaire) sont conservées en dehors de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] et sont susceptibles de changer ponctuellement, la fonction **AT TIME ZONE** est classée comme non déterministe. 

## <a name="examples"></a>Exemples

### <a name="a-add-target-time-zone-offset-to-datetime-without-offset-information"></a>R. Ajouter un décalage de fuseau horaire cible à la valeur datetime sans informations sur le décalage  

Utilisez **AT TIME ZONE** pour ajouter un décalage basé sur les règles de fuseau horaire quand vous savez que les valeurs **datetime** initiales sont fournies dans le même fuseau horaire :  

```sql
USE AdventureWorks2016;
GO  
  
SELECT SalesOrderID, OrderDate,
    OrderDate AT TIME ZONE 'Pacific Standard Time' AS OrderDate_TimeZonePST  
FROM Sales.SalesOrderHeader;
```

### <a name="b-convert-values-between-different-time-zones"></a>B. Convertir des valeurs entre des fuseaux horaires différents  

L’exemple suivant convertit les valeurs entre des fuseaux horaires différents :  

```sql
USE AdventureWorks2016;
GO

SELECT SalesOrderID, OrderDate,
    OrderDate AT TIME ZONE 'Pacific Standard Time' AS OrderDate_TimeZonePST,
    OrderDate AT TIME ZONE 'Central European Standard Time' AS OrderDate_TimeZoneCET
FROM Sales.SalesOrderHeader;
```

### <a name="c-query-temporal-tables-using-a-specific-time-zone"></a>C. Interroger des tables temporelles en utilisant un fuseau horaire spécifique

L’exemple suivant sélectionne des données d’une table temporelle en utilisant l’heure standard du Pacifique.  

```sql
USE AdventureWorks2016;
GO

DECLARE @ASOF datetimeoffset;  
SET @ASOF = DATEADD (month, -1, GETDATE()) AT TIME ZONE 'UTC';

-- Query state of the table a month ago projecting period
-- columns as Pacific Standard Time
SELECT BusinessEntityID, PersonType, NameStyle, Title,
    FirstName, MiddleName,
    ValidFrom AT TIME ZONE 'Pacific Standard Time'
FROM  Person.Person_Temporal
FOR SYSTEM_TIME AS OF @ASOF;
```

## <a name="next-steps"></a>Étapes suivantes

- [Types de date et d’heure](../../t-sql/data-types/date-and-time-types.md)
- [Types de données et fonctions de date et d’heure &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)