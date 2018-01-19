---
title: SUR le fuseau horaire (Transact-SQL) | Documents Microsoft
ms.date: 11/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AT TIME ZONE
- AT_TIME_ZONE_TSQL
helpviewer_keywords: AT TIME ZONE function
ms.assetid: 311f682f-7f1b-43b6-9ea0-24e36b64f73a
caps.latest.revision: "13"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: b9fc240d76c2939e0ed96d87fdbfee35ec8208ce
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="at-time-zone-transact-sql"></a>SUR le fuseau horaire (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Convertit un *inputdate* correspondant *datetimeoffset* valeur dans le fuseau horaire cible. Si *inputdate* est fourni sans informations de décalage, la fonction s’applique à l’offset du fuseau horaire en supposant que *inputdate* valeur est fournie dans le fuseau horaire cible. Si *inputdate* est fournie comme un *datetimeoffset* valeur, à **AT TIME ZONE** clause convertit en fuseau horaire cible à l’aide des règles de conversion de fuseau horaire.  
  
 **SUR fuseau horaire** implémentation s’appuie sur un mécanisme de Windows pour convertir **datetime** valeurs sur plusieurs fuseaux horaires.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inputdate AT TIME ZONE timezone  
```  
  
## <a name="arguments"></a>Arguments  
 *inputdate*  
 Est une expression qui peut être résolue en un **smalldatetime**, **datetime**, **datetime2**, ou **datetimeoffset** valeur.  
  
 *timezone*  
 Nom du fuseau horaire de destination. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]s’appuie sur fuseau horaire et sont stockés dans le Registre Windows. Tous les fuseaux horaires, installés sur l’ordinateur sont stockées dans la ruche de Registre suivante : **KEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones**. Une liste de fuseaux horaires installés est également exposée via le [sys.time_zone_info &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-time-zone-info-transact-sql.md) vue.  
  
## <a name="return-types"></a>Types de retour  
 Retourne le type de données **datetimeoffset**  
  
## <a name="return-value"></a>Valeur retournée  
 Le **datetimeoffset** valeur dans le fuseau horaire cible.  
  
## <a name="remarks"></a>Notes  
 **SUR fuseau horaire** applique des règles spécifiques pour la conversion des valeurs d’entrée dans **smalldatetime**, **datetime** et **datetime2** modifier les types de données qui appartiennent à un intervalle qui est affecté par l’heure d’été :  
  
-   Lorsque l’horloge est définie en avance, il y a un écart en heure locale qui durée dépend de la durée de l’ajustement de l’horloge (généralement 1 heure, mais il peut être 30 ou 45 minutes, en fonction du fuseau horaire). Dans ce cas, les points dans le temps qui appartiennent à cet intervalle sont convertis avec l’offset de *après* modification de l’heure d’été.  
  
    ```  
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
  
- Lorsque l’horloge est redéfini, heure locale de 2 heures se chevauchent sur une heure.  Dans ce cas, les points dans le temps qui appartiennent à l’intervalle avec chevauchement sont présentées avec le décalage *avant* la modification de l’horloge :  
  
    ```  
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

Étant donné que certaines informations (tels que les règles de fuseau horaire) sont conservées en dehors de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] et sont susceptibles de changer occasionnel, le **AT TIME ZONE** fonction classée comme non déterministes. 
  
## <a name="examples"></a>Exemples  
  
### <a name="a-add-target-time-zone-offset-to-datetime-without-offset-information"></a>A. Ajouter un décalage de fuseau horaire cible à la date/heure sans informations de décalage  
 Utilisez **AT TIME ZONE** pour ajouter l’offset en fonction de règles de fuseau horaire lorsque vous savez que l’original **datetime** valeurs sont fournies dans le même fuseau horaire :  
  
```  
USE AdventureWorks2016;  
GO  
  
SELECT SalesOrderID, OrderDate,   
    OrderDate AT TIME ZONE 'Pacific Standard Time' AS OrderDate_TimeZonePST  
FROM Sales.SalesOrderHeader;  
```  
  
### <a name="b-convert-values-between-different-time-zones"></a>B. Convertir des valeurs entre les différents fuseaux horaires  
 L’exemple suivant convertit les valeurs entre des fuseaux horaires différents :  
  
```  
USE AdventureWorks2016;  
GO  
  
SELECT SalesOrderID, OrderDate,   
    OrderDate AT TIME ZONE 'Pacific Standard Time' AS OrderDate_TimeZonePST,  
    OrderDate AT TIME ZONE 'Pacific Standard Time'   
    AT TIME ZONE 'Central European Standard Time' AS OrderDate_TimeZoneCET  
FROM Sales.SalesOrderHeader;  
```  
  
### <a name="c-query-temporal-tables-using-local-time-zone"></a>C. Interroger des Tables temporelles à l’aide du fuseau horaire local  
 L’exemple suivant sélectionne des données à partir d’une table temporelle.  
  
```  
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
  
## <a name="see-also"></a>Voir aussi  
 [Types de date et heure](../../t-sql/data-types/date-and-time-types.md)   
 [Données de date et heure les fonctions et Types de &#40; Transact-SQL &#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)  
  
  
