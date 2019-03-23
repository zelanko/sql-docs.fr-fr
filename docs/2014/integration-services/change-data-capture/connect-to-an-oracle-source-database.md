---
title: Connexion à une base de données source Oracle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- oraDb
ms.assetid: 220cf555-0db2-443c-8f87-8e413f3ca731
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f32462ef33af50a08cd933ed5c1a04c4efaa17de
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58377317"
---
# <a name="connect-to-an-oracle-source-database"></a>Connexion à une base de données source Oracle
  La page Source Oracle permet de fournir les informations nécessaires pour la connexion à la base de données source Oracle. L'instance de capture de données modifiées lit les journaux de restauration par progression de la base de données Oracle à laquelle vous êtes connecté.  
  
 **Chaîne de connexion Oracle**  
 Entrez la chaîne de connexion Oracle à l'ordinateur sur lequel est installée la base de données Oracle que vous utilisez. La chaîne de connexion est entrée de l'une des manières suivantes :  
  
 `host[:port][/service name]`  
  
 La chaîne de connexion peut également spécifier un descripteur de connexion Oracle Net, par exemple, `(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp) (HOST=erp.contoso.com) (PORT=1521)) (CONNECT_DATA=(SERVICE_NAME=orcl)))`  
  
 Si vous utilisez un serveur d'annuaire ou des noms TNS, la chaîne de connexion peut être le nom de la connexion.  
  
 **Authentification pour l'exploration de données de journaux Oracle**  
 Pour entrer les informations d'identification de l'utilisateur de la base de données Oracle qui est autorisé à explorer les données de journaux, sélectionnez l'une des options suivantes :  
  
-   **Authentification Windows** : sélectionnez cette option pour utiliser les informations d’identification actuelles de domaine Windows. Vous ne pouvez utiliser cette option que si la base de données Oracle est configurée pour utiliser l'authentification Windows.  
  
-   **Authentification Oracle** : si vous sélectionnez cette option, vous devez taper le **Nom d’utilisateur** et le **Mot de passe** de l’utilisateur dans la base de données Oracle à laquelle vous vous connectez.  
  
> [!NOTE]
>  Un utilisateur doit avoir les privilèges suivants dans la base de données Oracle de façon à être un utilisateur d'exploration de données de journaux.  
> 
>  -   SELECT sur \<tout_table_capturée>  
> -   SELECT ANY TRANSACTION  
> -   EXECUTE sur DBMS_LOGMNR  
> -   SELECT sur V$LOGMNR CONTENTS  
> -   SELECT sur V$ARCHIVED LOG  
> -   SELECT sur V$LOG  
> -   SELECT sur V$LOGFILE  
> -   SELECT sur V$DATABASE  
> -   SELECT sur V$THREAD  
> -   SELECT sur ALL INDEXES  
> -   SELECT sur ALL OBJECTS  
> -   SELECT sur DBA OBJECTS  
> -   SELECT sur ALL TABLES  
> 
>  Si l'un de ces privilèges ne peut pas être accordé à V$xxx, alors accordez-les à V_S$xxx.  
  
 **Tester la connexion**  
 Cliquez sur **Tester la connexion** pour déterminer si vous avez établi une connexion avec l’ordinateur distant sur lequel la base de données Oracle est installée. Une boîte de dialogue s'ouvre pour vous indiquer si la connexion a abouti.  
  
> [!IMPORTANT]  
>  En raison d'un problème connu, la connexion à la base de données source Oracle peut échouer si le concepteur CDC n'est pas exécuté en tant qu'administrateur. Si la connexion échoue, fermez et redémarrez le concepteur CDC à l'aide de l'option **Exécuter en tant qu'administrateur** .  
  
 Une fois les informations entrées sur cette page, cliquez sur **Suivant** pour [Select Oracle Tables and Columns](select-oracle-tables-and-columns.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : créer l'instance SQL Server de base de données de modifications](how-to-create-the-sql-server-change-database-instance.md)   
 [Modifier les propriétés d'instance](edit-instance-properties.md)  
  
  
