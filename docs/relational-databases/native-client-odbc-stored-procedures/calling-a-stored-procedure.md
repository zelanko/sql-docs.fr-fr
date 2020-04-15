---
title: Appel à une procédure stockée (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- ODBC, stored procedures
- stored procedures [ODBC], calling
- SQL Server Native Client ODBC driver, stored procedures
- ODBC CALL escape sequence
- escape sequences [SQL Server]
- CALL statement
ms.assetid: d13737f4-f641-45bf-b56c-523e2ffc080f
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1fae2e947d0faa38ae875f72b48119b21c30dd47
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304566"
---
# <a name="calling-a-stored-procedure"></a>Appel d'une procédure stockée
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conducteur de Native Client ODBC prend en [!INCLUDE[tsql](../../includes/tsql-md.md)]charge à la fois la séquence d’évacuation ODBC CALL et la déclaration [EXECUTE](../../t-sql/language-elements/execute-transact-sql.md) pour l’exécution des procédures stockées; la séquence d’évacuation ODBC CALL est la méthode préférée. L'utilisation de la syntaxe ODBC permet à une application de récupérer les codes de retour de procédures stockées et le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est également optimisé pour utiliser un protocole initialement développé pour envoyer des appels de procédure distante (RPC) entre des ordinateurs qui exécutent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ce protocole RPC augmente les performances en supprimant une bonne partie du traitement des paramètres et de l'analyse des instructions sur le serveur.  
  
> [!NOTE]  
>  Lors [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l’appel des procédures stockées en utilisant des paramètres nommés avec ODBC (pour plus d’informations, voir [Paramètres de liaison par nom (Paramètres nommés)](https://go.microsoft.com/fwlink/?LinkID=209721)), les noms de paramètres doivent commencer par le «\@caractère ». Il s'agit d'une restriction spécifique à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client applique cette restriction plus strictement que MDAC (Microsoft Data Access Components).  
  
 La séquence d'échappement ODBC CALL permettant d'appeler une procédure est la suivante :  
  
 Appeler **?=****call**_procedure_name_[[[[[paramètre]*parameter*[**[ [ [***[paramètre]...).*  
  
 où *procedure_name* spécifie le nom d’une procédure et *le paramètre* spécifie un paramètre de procédure. Les paramètres nommés sont pris en charge uniquement dans les instructions à l'aide de la séquence d'échappement ODBC CALL.  
  
 Une procédure peut avoir zéro, un ou plusieurs paramètres. Elle peut également retourner une valeur (comme l'indique le marqueur de paramètre optionnel ?= au début de la syntaxe). Si un paramètre est un paramètre d'entrée ou d'entrée/sortie, ce peut être un littéral ou un marqueur de paramètre. Si le paramètre est un paramètre de sortie, ce doit être un marqueur de paramètre car la sortie est inconnue. Les marqueurs de paramètres doivent être reliés à [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) avant l’exécution de la déclaration d’appel de la procédure.  
  
 Les paramètres d'entrée et d'entrée/sortie peuvent être omis dans les appels de procédure. Si une procédure est appelée avec des parenthèses mais sans paramètre, le pilote instruit la source de données d'utiliser la valeur par défaut comme premier paramètre. Par exemple :  
  
 procedure_name**d’appel** _procedure_name_**( )**  
  
 Si la procédure n'a pas de paramètre, elle peut échouer. Si une procédure est appelée sans parenthèses, le pilote n'envoie aucune valeur de paramètre. Par exemple :  
  
 -**procedure_name d’appel** _procedure_name_  
  
 Des littéraux peuvent être spécifiés comme paramètres d'entrée et d'entrée/sortie dans les appels de procédure. Par exemple, la procédure InsertOrder possède cinq paramètres d'entrée. L'appel suivant à InsertOrder omet le premier paramètre, fournit un littéral pour le deuxième paramètre et utilise un marqueur de paramètre pour les troisième, quatrième et cinquième paramètres. (Les paramètres sont numérotés de façon séquentielle, en commençant par la valeur 1.)  
  
```  
{call InsertOrder(, 10, ?, ?, ?)}  
```  
  
 Notez que si un paramètre est omis, la virgule qui le sépare des autres paramètres doit encore apparaître. Si un paramètre d'entrée ou d'entrée/sortie est omis, la procédure utilise la valeur par défaut du paramètre. D'autres façons de spécifier la valeur par défaut d'un paramètre d'entrée ou d'entrée/sortie consistent à affecter la valeur SQL_DEFAULT_PARAM à la mémoire tampon de l'indicateur/longueur associée au paramètre ou à utiliser le mot clé DEFAULT.  
  
 Si un paramètre d'entrée/sortie est omis ou si un littéral est fourni comme paramètre, le pilote ignore la valeur de sortie. De la même façon, si le marqueur de paramètre pour la valeur de retour d'une procédure est omis, le pilote ignore la valeur de retour. Enfin, si une application spécifie un paramètre de valeur de retour pour une procédure qui ne renvoie pas de valeur, le pilote affecte la valeur SQL_NULL_DATA à la mémoire tampon de l'indicateur/longueur associée au paramètre.  
  
## <a name="delimiters-in-call-statements"></a>Délimiteurs dans les instructions CALL  
 Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge par défaut également une option de compatibilité spécifique à la séquence d'échappement ODBC { CALL }. Le pilote accepte les instructions CALL avec un jeu unique de guillemets doubles délimitant le nom complet de la procédure stockée :  
  
```  
{ CALL "master.dbo.sp_who" }  
```  
  
 Par défaut, le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client accepte également des instructions CALL qui suivent les règles ISO et mettent chaque identificateur entre guillemets doubles :  
  
```  
{ CALL "master"."dbo"."sp_who" }  
```  
  
 Lors d'une exécution avec les paramètres par défaut, toutefois, le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ne prend pas en charge l'utilisation de l'une ou de l'autre forme d'identificateurs entre guillemets avec des identificateurs qui contiennent des caractères non spécifiés comme légaux dans des identificateurs définis par la norme ISO. Par exemple, le conducteur ne peut pas accéder à une procédure stockée nommée **"My.Proc"** à l’aide d’une déclaration CALL avec des identifiants cités:  
  
```  
{ CALL "MyDB"."MyOwner"."My.Proc" }  
```  
  
 Cette instruction est interprétée par le pilote comme :  
  
```  
{ CALL MyDB.MyOwner.My.Proc }  
```  
  
 Le serveur soulève une erreur qu’un serveur lié nommé **MyDB** n’existe pas.  
  
 Ce problème ne se pose pas lors de l'utilisation d'identificateurs entre parenthèses et l'instruction suivante est interprétée correctement :  
  
```  
{ CALL [MyDB].[MyOwner].[My.Table] }  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de procédures stockées](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
