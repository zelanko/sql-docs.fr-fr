---
title: Utilitaire SqlLocalDB | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- SqlLocalDB utility [SQL Server]
- local database runtime utility
- LocalDB, SqlLocalDB Utility
ms.assetid: d785cdb7-1ea0-4871-bde9-1ae7881190f5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f13a16e7c8f507914abe8529e02b76161072c5bc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63035398"
---
# <a name="sqllocaldb-utility"></a>Utilitaire SqlLocalDB
  Utilisez l' `SqlLocalDB` utilitaire pour créer une instance de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssExpCurrent](../includes/ssexpcurrent-md.md)]base de données **locale.** L' `SqlLocalDB` utilitaire (SqlLocalDB. exe) est un outil en ligne de commande simple pour permettre aux utilisateurs et aux développeurs de créer et [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **de gérer une instance de base**de données locale. Pour plus d’informations sur l’utilisation de la **base de données locale, consultez** [SQL Server 2014 Express](../database-engine/configure-windows/sql-server-2016-express-localdb.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SqlLocalDB.exe   
{  
      [ create   | c ] <instance-name><instance-version> [-s ]  
    | [ delete   | d ] <instance-name>  
    | [ start    | s ] <instance-name>  
    | [ stop     | p ] <instance-name>  [ -i ] [ -k ]  
    | [ share    | h ] ["<user_SID>" | "<user_account>" ] "<private-name>""<shared-name>"  
    | [ unshare  | u ] "<shared-name>"  
    | [ info     | i ] <instance-name>  
    | [ versions | v ]  
    | [ trace    | t ] [ on | off ]  
    | [ help     | -? ]  
}  
```  
  
## <a name="arguments"></a>Arguments  
 [ **Create** | **c** ] instance- * \<Name>instance-version>* [**-s** ] * \<*  
 Crée une instance de [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**. `SqlLocalDB`utilise la version des [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] fichiers binaires spécifiée par * \<l’argument>version* de l’instance. Le numéro de version est spécifié au format numérique avec au moins une décimale. Les numéros de version secondaire (Service Packs) sont facultatifs. Par exemple, les deux numéros de version suivants sont acceptables : 11.0 et 11.0.1186. La version spécifiée doit être installée sur l'ordinateur. S’il n’est pas spécifié, le numéro de version est défini par `SqlLocalDB` défaut sur la version de l’utilitaire. L’ajout de **-s** permet de démarrer la nouvelle instance de **LocalDB**.  
  
 [ **partage** | **h** ]  
 Partage l’instance privée spécifiée de **LocalDB** à l’aide du nom partagé spécifié. Si le SID ou le nom de compte de l'utilisateur est omis, il prend par défaut la valeur de l'utilisateur actuel.  
  
 [ **** | **u** non partagé  
 Arrête le partage de l’instance partagée spécifiée de **LocalDB**.  
  
 [ **supprimer** | **d** ] *nom de l’instance>\<*  
 Supprime l’instance spécifiée de [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.  
  
 [ **Démarrer** | les**s** ] «*\<nom d’instance>*»  
 Démarre l’instance spécifiée de [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**. En cas de réussite de l'opération, l'instruction retourne l'adresse du canal nommé de **LocalDB**.  
  
 [ **Stop** | **p** ] *nom de l’instance>[-i] [-k] \<* **** ****  
 Arrête l’instance spécifiée de [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**. Ajout **de-i** demande l’arrêt de l' `NOWAIT` instance avec l’option. L’ajout de **-k** met fin au processus de l’instance sans le contacter.  
  
 [ **info** | **i** ] [ * \<nom-instance>* ]  
 Répertorie toutes les instances de [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** détenues par l’utilisateur actuel.  
  
 nom de l' [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] *instance>retourne le nom, la version, l’État (en cours d’exécution ou arrêté), la dernière heure de début pour l’instance spécifiée de la base de données locale et le nom du canal local de la base de données \<* **locale.** ****  
  
 [ **trace** | **t** ]  | **désactivé** ****  
 **trace on** active le suivi des `SqlLocalDB` appels d’API pour l’utilisateur actuel. **trace OFF** désactive le suivi.  
  
 **-?**  
 Retourne une brève description de `SqlLocalDB` chaque option.  
  
## <a name="remarks"></a>Notes  
 L’argument *instance name* doit respecter les règles applicables aux identificateurs [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou il doit être placé entre guillemets.  
  
 L’exécution de SqlLocalDB sans arguments retourne le texte d’aide.  
  
 Les opérations autres que le démarrage peuvent être exécutées sur une instance appartenant à l'utilisateur actuellement connecté.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-an-instance-of-localdb"></a>R. Création d'une instance de LocalDB  
 L’exemple suivant crée une instance de [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** nommée `DEPARTMENT` utilisant les binaires [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] et démarre l’instance.  
  
```  
SqlLocalDB.exe create "DEPARTMENT" 12.0 -s  
```  
  
### <a name="b-working-with-a-shared-instance-of-localdb"></a>B. Utilisation d'une instance partagée de LocalDB  
 Ouvrez une invite de commandes en utilisant des autorisations d'administrateur.  
  
```  
SqlLocalDB.exe create "DeptLocalDB"  
SqlLocalDB.exe share "DeptLocalDB" "DeptSharedLocalDB"  
SqlLocalDB.exe start "DeptLocalDB"  
SqlLocalDB.exe info "DeptLocalDB"  
REM The previous statement outputs the Instance pipe name for the next step  
sqlcmd -S np:\\.\pipe\LOCALDB#<use your pipe name>\tsql\query  
CREATE LOGIN NewLogin WITH PASSWORD = 'Passw0rd!!@52';   
GO  
CREATE USER NewLogin;  
GO  
EXIT  
```  
  
 Exécutez le code suivant pour vous connecter à l'instance partagée de **LocalDB** à l'aide de la connexion `NewLogin` .  
  
```  
sqlcmd -S (localdb)\.\DeptSharedLocalDB -U NewLogin -P Passw0rd!!@52  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server 2014 Express LocalDB](../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
  
