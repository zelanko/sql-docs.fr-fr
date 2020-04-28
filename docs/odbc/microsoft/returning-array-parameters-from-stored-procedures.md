---
title: Retour de paramètres de tableau à partir de procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 2018069b-da5d-4cee-a971-991897d4f7b5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bc998dadc0e0c4a4bfe054bfd1d40296bc176393
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81292859"
---
# <a name="returning-array-parameters-from-stored-procedures"></a>Retour de paramètres de tableau depuis des procédures stockées
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Dans Oracle 7,3, il n’existe aucun moyen d’accéder à un type d’enregistrement PL/SQL, sauf à partir d’un programme PL/SQL. Si une procédure ou une fonction packagée a un argument formel défini en tant que type d’enregistrement PL/SQL, il n’est pas possible de lier cet argument formel en tant que paramètre. Utilisez le type de TABLE PL/SQL dans le pilote Microsoft ODBC pour Oracle pour appeler des paramètres de tableau à partir de procédures contenant les séquences d’échappement appropriées.  
  
 Pour appeler la procédure, utilisez la syntaxe suivante :  
  
```  
{call  <package-name>.<proc-or-func>;  
(..., {resultset <max-records-requested> ,<formal-array-param_1>,;  
 <formal-array-param_2>,...,<formal-array-param_n> }, ... ) }  
```  
  
> [!NOTE]  
>  Le \<paramètre Max-recordss-requested> doit être supérieur ou égal au nombre de lignes présentes dans le jeu de résultats. Dans le cas contraire, Oracle retourne une erreur qui est transmise à l’utilisateur par le pilote.  
>   
>  Les enregistrements PL/SQL ne peuvent pas être utilisés en tant que paramètres de tableau. Chaque paramètre de tableau ne peut représenter qu’une seule colonne d’une table de base de données.  
  
 L’exemple suivant définit un package contenant deux procédures qui retournent des jeux de résultats différents, puis fournit deux manières de retourner des jeux de résultats à partir du package.  
  
## <a name="package-definition"></a>Définition du package :  
  
```  
CREATE OR REPLACE PACKAGE SimplePackage AS  
  
TYPE t_id is TABLE of  NUMBER(5)  
    INDEX BY BINARY_INTEGER;  
  
TYPE t_Course is TABLE of VARCHAR2(10)  
    INDEX BY BINARY_INTEGER;  
  
TYPE t_Dept is TABLE of VARCHAR2(5)  
    INDEX BY BINARY_INTEGER;  
  
PROCEDURE proc1  
   (  
   o_id             OUT    t_id,  
   ao_course       OUT    t_Course,  
   ao_dept         OUT    t_Dept  
   );  
  
TYPE t_pk1Type1 IS TABLE OF VARCHAR2(100) INDEX BY BINARY_INTEGER;  
TYPE t_pk1Type2 IS TABLE OF NUMBER INDEX BY BINARY_INTEGER;  
PROCEDURE proc2  
   (  
   i_Arg1         IN    NUMBER,  
   ao_Arg2         OUT   t_pk1Type1,  
   ao_Arg3         OUT   t_pk1Type2  
   );  
  
END SimplePackage;  
  
CREATE OR REPLACE PACKAGE BODY SimplePackage AS  
    PROCEDURE  proc1 ( o_id OUT t_id,  
    ao_course OUT t_Course, ao_dept OUT t_Dept   ) AS  
    BEGIN  
          o_id(1):= 200;  
          ao_course(1) :=  'M101';  
          ao_dept(1) :=  'EEE' ;  
  
          o_id(2) := 201;  
          ao_course(2) :=  'PHY320';  
          ao_dept(2) :=  'ECE' ;  
  
     END proc1;  
PROCEDURE proc2  
   (  
   i_Arg1         IN    NUMBER,  
   ao_Arg2         OUT   t_pk1Type1,  
   ao_Arg3         OUT   t_pk1Type2  
   )  
AS  
   i   NUMBER;  
BEGIN  
   FOR i IN 1 .. i_Arg1 LOOP  
      ao_Arg2(i) := 'Row Number ' || to_char(i);  
   END LOOP;  
   FOR i IN 1 .. i_Arg1 LOOP  
      ao_Arg3(i) := i;  
   END LOOP;  
END proc2;  
END SimplePackage;  
```  
  
#### <a name="to-invoke-procedure-proc1"></a>Pour appeler la procédure PROC1  
  
1.  Retourne toutes les colonnes dans un seul jeu de résultats :  
  
    ```  
    {call SimplePackage.Proc1( {resultset  3, o_id , ao_course, ao_dept  } ) }  
    ```  
  
2.  Retourne chaque colonne sous la forme d’un seul jeu de résultats :  
  
    ```  
    {call SimplePackage.Proc1( {resultset 3, o_id},  {resultset 3, ao_course}, {resultset 3, ao_dept} ) }  
    ```  
  
     Cela retourne trois jeux de résultats, un pour chaque colonne.  
  
#### <a name="to-invoke-procedure-proc2"></a>Pour appeler la procédure PROC2  
  
1.  Retourne toutes les colonnes dans un seul jeu de résultats :  
  
    ```  
    {call SimplePackage.Proc2( 5 , {resultset  5, ao_Arg2, ao_Arg3} ) }  
    ```  
  
2.  Retourne chaque colonne sous la forme d’un seul jeu de résultats :  
  
    ```  
    {call SimplePackage.Proc2( 5 , {resultset 5, ao_Arg2}, {resultset 5, ao_Arg3} ) }  
    ```  
  
 Assurez-vous que vos applications récupèrent tous les jeux de résultats à l’aide de l’API [SQLMoreResults](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) . Pour plus d’informations, reportez-vous au *Guide de référence du programmeur ODBC*.  
  
> [!NOTE]  
>  Dans le pilote ODBC pour Oracle version 2,0, les fonctions Oracle qui retournent des tableaux PL/SQL ne peuvent pas être utilisées pour retourner des jeux de résultats.
