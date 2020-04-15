---
title: Effets des options ISO (fr) Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ISO options (ODBC)
- ODBC applications, ISO options
- ODBC applications, statements
- SQL Server Native Client ODBC driver, ISO options
- statements [ODBC], ISO options
ms.assetid: 813f1397-fa0b-45ec-a718-e13fe2fb88ac
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: adf37d03f5ea4f06be4d58e60deca68e10d45abb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297932"
---
# <a name="effects-of-iso-options"></a>Conséquences des options ISO
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le standard ODBC est étroitement mis en correspondance avec la norme ISO, et les applications ODBC attendent un comportement standard d'un pilote ODBC. Pour rendre son comportement plus étroitement conforme à celui [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] défini dans la norme ODBC, le pilote Native Client ODBC utilise toujours toutes les options ISO disponibles dans la version de SQL Server avec laquelle il se connecte.  
  
 Lorsque [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] le pilote native Client ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]se connecte à une instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de , le serveur détecte que le client utilise le pilote native ODBC client et définit plusieurs options sur.  
  
 Le pilote émet ces instructions lui-même ; l'application ODBC n'émet aucune demande. La définition de ces options permet aux applications ODBC utilisant le pilote d'être plus portables parce que le comportement du serveur correspond alors à la norme ISO.  
  
 Les applications basées sur DB-Library n'activent généralement pas ces options. Les sites qui observent un comportement différent entre les clients de l’ODBC ou [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de DB-Library lorsqu’ils exécutent la même déclaration SQL ne devraient pas présumer que cela indique un problème avec le conducteur de l’ODBC du client autochtone. Ils devraient d’abord réexécuter l’énoncé dans l’environnement DB-Library avec les mêmes options SET que ce qui serait utilisé par le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] chauffeur native ODBC.  
  
 Comme les options SET peuvent être activées et désactivées à tout moment par les utilisateurs et les applications, les développeurs de procédures stockées et de déclencheurs doivent aussi veiller à tester leurs procédures et leurs déclencheurs avec les options SET répertoriées ci-dessus activées et désactivées. Cela garantit que les procédures et les déclencheurs fonctionnent correctement, quelles que soient les options activées d'une connexion donnée lors de l'appel du déclencheur. Les déclencheurs ou les procédures stockées qui requièrent un paramètre particulier pour l'une de ces options doivent émettre une instruction SET au démarrage du déclencheur ou de la procédure stockée. Cette instruction SET n'est active que pour l'exécution du déclencheur ou de la procédure stockée ; à la fin de la procédure ou du déclencheur, la configuration d'origine est restaurée.  
  
 En cas de connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], une quatrième option SET, CONCAT_NULL_YIELDS_NULL, est également activée. Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote native Client ODBC ne fixe pas ces options si AnsiNPW-NO est spécifié dans la source de données ou sur [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) ou [SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md).  
  
 Comme les options ISO [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mentionnées précédemment, le pilote native Client ODBC ne tourne pas l’option QUOTED_IDENTIFIER si QuotedID-NO est spécifié dans la source de données ou sur **SQLDriverConnect** ou **SQLBrowseConnect**.  
  
 Pour permettre au pilote de connaître l'état actuel des options SET, les applications ODBC ne doivent pas utiliser l'instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] SET pour définir ces options. Elles doivent uniquement définir ces options à l'aide de la source de données ou des options de connexion. Si l'application émet des instructions SET, le pilote peut générer des instructions SQL inexactes.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution des déclarations &#40;&#41;ODBC](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)   
 [SQLDriverConnect (SQLDriverConnect)](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md)   
 [SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)  
  
  
