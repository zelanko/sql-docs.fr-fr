---
title: Appel d’une procédure stockée | Microsoft Docs
description: En savoir plus sur la séquence d’échappement ODBC CALL, la méthode recommandée pour exécuter des procédures stockées. Le pilote ODBC Native Client prend également en charge Transact-SQLEXECUTE.
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
ms.openlocfilehash: 2a8ebd8eb539190c65e1e1a97ce55579eb93f180
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86004654"
---
# <a name="calling-a-stored-procedure"></a>Appel d'une procédure stockée
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge à la fois la séquence d’échappement ODBC Call et l' [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction [Execute](../../t-sql/language-elements/execute-transact-sql.md) pour exécuter des procédures stockées ; la séquence d’échappement ODBC Call est la méthode recommandée. L'utilisation de la syntaxe ODBC permet à une application de récupérer les codes de retour de procédures stockées et le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est également optimisé pour utiliser un protocole initialement développé pour envoyer des appels de procédure distante (RPC) entre des ordinateurs qui exécutent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ce protocole RPC augmente les performances en supprimant une bonne partie du traitement des paramètres et de l'analyse des instructions sur le serveur.  
  
> [!NOTE]  
>  Lors [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l’appel de procédures stockées à l’aide de paramètres nommés avec ODBC (pour plus d’informations, consultez [liaison de paramètres par nom (paramètres nommés)](https://go.microsoft.com/fwlink/?LinkID=209721)), les noms de paramètres doivent commencer par le \@ caractère «». Il s'agit d'une restriction spécifique à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client applique cette restriction plus strictement que MDAC (Microsoft Data Access Components).  
  
 La séquence d'échappement ODBC CALL permettant d'appeler une procédure est la suivante :  
  
 {[**? =**]**appel**_PROCEDURE_NAME_[([*paramètre*] [**,**[*paramètre*]]...)]}  
  
 où *PROCEDURE_NAME* spécifie le nom d’une procédure et un *paramètre* spécifie un paramètre de procédure. Les paramètres nommés sont pris en charge uniquement dans les instructions à l'aide de la séquence d'échappement ODBC CALL.  
  
 Une procédure peut avoir zéro, un ou plusieurs paramètres. Elle peut également retourner une valeur (comme l'indique le marqueur de paramètre optionnel ?= au début de la syntaxe). Si un paramètre est un paramètre d'entrée ou d'entrée/sortie, ce peut être un littéral ou un marqueur de paramètre. Si le paramètre est un paramètre de sortie, ce doit être un marqueur de paramètre car la sortie est inconnue. Les marqueurs de paramètres doivent être liés à [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) avant l’exécution de l’instruction d’appel de procédure.  
  
 Les paramètres d'entrée et d'entrée/sortie peuvent être omis dans les appels de procédure. Si une procédure est appelée avec des parenthèses mais sans paramètre, le pilote instruit la source de données d'utiliser la valeur par défaut comme premier paramètre. Par exemple :  
  
 {**call** _PROCEDURE_NAME_**()**}  
  
 Si la procédure n'a pas de paramètre, elle peut échouer. Si une procédure est appelée sans parenthèses, le pilote n'envoie aucune valeur de paramètre. Par exemple :  
  
 {**call** _PROCEDURE_NAME_}  
  
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
  
 Lors d'une exécution avec les paramètres par défaut, toutefois, le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ne prend pas en charge l'utilisation de l'une ou de l'autre forme d'identificateurs entre guillemets avec des identificateurs qui contiennent des caractères non spécifiés comme légaux dans des identificateurs définis par la norme ISO. Par exemple, le pilote ne peut pas accéder à une procédure stockée nommée **« My. proc »** à l’aide d’une instruction call avec des identificateurs entre guillemets :  
  
```  
{ CALL "MyDB"."MyOwner"."My.Proc" }  
```  
  
 Cette instruction est interprétée par le pilote comme :  
  
```  
{ CALL MyDB.MyOwner.My.Proc }  
```  
  
 Le serveur génère une erreur indiquant qu’un serveur lié nommé **MyDB** n’existe pas.  
  
 Ce problème ne se pose pas lors de l'utilisation d'identificateurs entre parenthèses et l'instruction suivante est interprétée correctement :  
  
```  
{ CALL [MyDB].[MyOwner].[My.Table] }  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de procédures stockées](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
