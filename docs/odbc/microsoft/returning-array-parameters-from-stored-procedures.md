---
title: Retour des paramètres de tableau des procédures stockées (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292859"
---
# <a name="returning-array-parameters-from-stored-procedures"></a>Retour de paramètres de tableau depuis des procédures stockées
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Dans Oracle 7.3, il n’y a aucun moyen d’accéder à un type d’enregistrement PL/SQL, sauf à partir d’un programme PL/SQL. Si une procédure ou une fonction emballée a un argument formel défini comme un type de dossier PL/SQL, il n’est pas possible de lier cet argument formel comme paramètre. Utilisez le type PL/SQL TABLE dans le microsoft ODBC Driver pour Oracle pour invoquer les paramètres de tableau des procédures contenant les séquences d’évacuation correctes.  
  
 Pour invoquer la procédure, utilisez la syntaxe suivante :  
  
```  
{call  <package-name>.<proc-or-func>;  
(..., {resultset <max-records-requested> ,<formal-array-param_1>,;  
 <formal-array-param_2>,...,<formal-array-param_n> }, ... ) }  
```  
  
> [!NOTE]  
>  Le \<paramètre> demandé par les enregistrements maximaux doit être supérieur ou égal au nombre de lignes présentes dans l’ensemble de résultats. Sinon, Oracle renvoie une erreur qui est transmise à l’utilisateur par le pilote.  
>   
>  Les enregistrements PL/SQL ne peuvent pas être utilisés comme paramètres de tableau. Chaque paramètre de tableau ne peut représenter qu’une colonne d’une table de base de données.  
  
 L’exemple suivant définit un paquet contenant deux procédures qui renvoient des ensembles de résultats différents, puis fournit deux façons de retourner les ensembles de résultats de l’ensemble.  
  
## <a name="package-definition"></a>Définition du paquet :  
  
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
  
#### <a name="to-invoke-procedure-proc1"></a>Invoquer la procédure PROC1  
  
1.  Retournez toutes les colonnes dans un seul ensemble de résultats :  
  
    ```  
    {call SimplePackage.Proc1( {resultset  3, o_id , ao_course, ao_dept  } ) }  
    ```  
  
2.  Ren retournons chaque colonne en un seul ensemble de résultats :  
  
    ```  
    {call SimplePackage.Proc1( {resultset 3, o_id},  {resultset 3, ao_course}, {resultset 3, ao_dept} ) }  
    ```  
  
     Cela renvoie trois ensembles de résultats, un pour chaque colonne.  
  
#### <a name="to-invoke-procedure-proc2"></a>Invoquer la procédure PROC2  
  
1.  Retournez toutes les colonnes dans un seul ensemble de résultats :  
  
    ```  
    {call SimplePackage.Proc2( 5 , {resultset  5, ao_Arg2, ao_Arg3} ) }  
    ```  
  
2.  Ren retournons chaque colonne en un seul ensemble de résultats :  
  
    ```  
    {call SimplePackage.Proc2( 5 , {resultset 5, ao_Arg2}, {resultset 5, ao_Arg3} ) }  
    ```  
  
 Assurez-vous que vos applications récupèrent tous les ensembles de résultats à l’aide de [l’API SQLMoreResults.](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) Pour plus d’informations, consultez la *référence du programmeur de l’ODBC*.  
  
> [!NOTE]  
>  Dans la version 2.0 D’ODBC Driver for Oracle, Oracle fonctionne que les tableaux PL/SQL de retour ne peuvent pas être utilisés pour retourner les ensembles de résultats.
