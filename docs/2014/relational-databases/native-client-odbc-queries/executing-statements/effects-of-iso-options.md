---
title: Effets des options ISO | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ebef85cf1deb2327122edfd536991f689b14c747
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68206762"
---
# <a name="effects-of-iso-options"></a>Conséquences des options ISO
  Le standard ODBC est étroitement mis en correspondance avec la norme ISO, et les applications ODBC attendent un comportement standard d'un pilote ODBC. Pour que son comportement soit conforme à celui défini dans la norme ODBC, le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client utilise toujours les options ISO disponibles dans la version de SQL Server avec laquelle il se connecte.  
  
 Lorsque le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC native client se connecte à une [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]instance de, le serveur détecte que le client utilise le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client et définit plusieurs options sur.  
  
 Le pilote émet ces instructions lui-même ; l'application ODBC n'émet aucune demande. La définition de ces options permet aux applications ODBC utilisant le pilote d'être plus portables parce que le comportement du serveur correspond alors à la norme ISO.  
  
 Les applications basées sur DB-Library n'activent généralement pas ces options. Les sites qui observent un comportement différent entre les clients ODBC ou DB-Library lorsqu’ils exécutent la même instruction SQL ne doivent pas [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supposer que ce problème est lié au pilote ODBC Native Client. Ils doivent d’abord réexécuter l’instruction dans l’environnement DB-Library avec les mêmes options SET que celles utilisées par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] le pilote ODBC Native Client.  
  
 Comme les options SET peuvent être activées et désactivées à tout moment par les utilisateurs et les applications, les développeurs de procédures stockées et de déclencheurs doivent aussi veiller à tester leurs procédures et leurs déclencheurs avec les options SET répertoriées ci-dessus activées et désactivées. Cela garantit que les procédures et les déclencheurs fonctionnent correctement, quelles que soient les options activées d'une connexion donnée lors de l'appel du déclencheur. Les déclencheurs ou les procédures stockées qui requièrent un paramètre particulier pour l'une de ces options doivent émettre une instruction SET au démarrage du déclencheur ou de la procédure stockée. Cette instruction SET n'est active que pour l'exécution du déclencheur ou de la procédure stockée ; à la fin de la procédure ou du déclencheur, la configuration d'origine est restaurée.  
  
 En cas de connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], une quatrième option SET, CONCAT_NULL_YIELDS_NULL, est également activée. Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client ne définit pas ces options sur si ANSINPW = no est spécifié dans la source de données ou sur [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) ou [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md).  
  
 À l’instar des options ISO indiquées [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] précédemment, le pilote ODBC Native Client n’active pas l’option QUOTED_IDENTIFIER si QUOTEDID = no est spécifié dans la source de données ou sur **SQLDriverConnect** ou **SQLBrowseConnect**.  
  
 Pour permettre au pilote de connaître l'état actuel des options SET, les applications ODBC ne doivent pas utiliser l'instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] SET pour définir ces options. Elles doivent uniquement définir ces options à l'aide de la source de données ou des options de connexion. Si l'application émet des instructions SET, le pilote peut générer des instructions SQL inexactes.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution d’instructions &#40;ODBC&#41;](executing-statements-odbc.md)   
 [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md)   
 [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md)  
  
  
