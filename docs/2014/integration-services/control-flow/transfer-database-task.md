---
title: Transfert de bases de données, tâche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.f1
helpviewer_keywords:
- Transfer Database task [Integration Services]
ms.assetid: b9a2e460-cdbc-458f-8df8-06b8b2de3d67
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 43a4f930b93d8657bdb5c2d0f91d7e6680b9ade2
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84918000"
---
# <a name="transfer-database-task"></a>Tâche de transfert de bases de données
  La tâche de transfert de bases de données transfère une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entre deux instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Contrairement aux autres tâches qui ne transfèrent les objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qu'en les copiant, la tâche de transfert de base de données peut copier ou déplacer une base de données. Cette tâche peut également servir à copier une base de données sur le même serveur.  
  
## <a name="offline-and-online-modes"></a>Modes en ligne et hors connexion  
 La base de données peut être transférée à l'aide du mode en ligne ou hors connexion. Lorsque vous utilisez le mode en ligne, la base de données reste attachée et est transférée à l'aide de SMO (SQL Management Object) pour copier les objets de base de données. Lorsque vous utilisez le mode hors connexion, la base de données est détachée, les fichiers de base de données sont copiés ou déplacés, et la base de données est attachée à la destination après que le transfert se soit terminé avec succès. Si la base de données est copiée, elle est automatiquement rattachée à la source si la copie a réussi. En mode hors connexion, la base de données est copiée plus rapidement, mais elle n'est pas disponible aux utilisateurs pendant le transfert.  
  
 Le mode hors connexion requiert la spécification des partages de fichiers réseau sur les serveurs source et destination contenant les fichiers de base de données. Si le dossier est partagé et est accessible à l’utilisateur, vous pouvez référencer le partage réseau à l’aide de la syntaxe \\\nom_ordinateur\Program Files\mon_dossier\\\. Sinon, vous devez utiliser la syntaxe \\\nom_ordinateur\c$\Program Files\mon_dossier\\\. Pour utiliser la dernière syntaxe, l'utilisateur doit avoir un accès en écriture vers les partages réseau source et destination.  
  
## <a name="transfer-of-databases-between-versions-of-sql-server"></a>Transférer des bases de données entre des versions de SQL Server  
 La tâche de transfert de bases de données peut transférer une base de données entre des instances de différentes versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="events"></a>Événements  
 La tâche de transfert de bases de données n'indique pas les stades intermédiaires de l'avancement du transfert des messages d'erreur : elle signale la tâche comme réalisée à 0 % ou à 100 %.  
  
## <a name="execution-value"></a>Valeur d'exécution  
 La valeur d'exécution, définie dans la propriété `ExecutionValue` de la tâche, renvoie la valeur 1, car contrairement aux autres tâches de transfert, la tâche de transfert de bases de données ne peut transférer qu'une seule base de données.  
  
 En affectant une variable définie par l'utilisateur à la propriété `ExecValueVariable` de la tâche de transfert de bases de données, les informations sur le transfert de messages d'erreur peuvent être rendues disponibles aux autres objets du package. Pour plus d’informations, consultez [Variables Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md) et [Utiliser des variables dans des packages](../use-variables-in-packages.md).  
  
## <a name="log-entries"></a>Entrées du journal  
 La tâche de transfert de bases de données comporte les entrées de journal personnalisées suivantes :  
  
-   SourceSQLServer    Cette entrée du journal indique le nom du serveur source.  
  
-   DestSQLServer    Cette entrée du journal indique le nom du serveur de destination.  
  
-   SourceDB    Cette entrée du journal indique le nom de la base de données transférée.  
  
 En outre, une entrée de journal pour l'événement `OnInformation` est écrite lorsque la base de données de destination est remplacée.  
  
## <a name="security-and-permissions"></a>Sécurité et autorisations  
 Pour transférer une base de données à l'aide du mode hors connexion, l'utilisateur qui exécute le package doit être un membre du rôle de serveur sysadmin.  
  
 Pour transférer une base de données à l'aide du mode en ligne, l'utilisateur qui exécute le package doit être un membre du rôle de serveur sysadmin ou le propriétaire (dbo) de la base de données sélectionnée.  
  
## <a name="configuration-of-the-transfer-database-task"></a>Configuration de la tâche de transfert de bases de données  
 Vous pouvez spécifier si la tâche doit tenter de rattacher la base de données source lorsque le transfert de base de données échoue.  
  
 La tâche de transfert de base de données peut également être configurée afin de permettre le remplacement d'une base de données de destination portant le même nom.  
  
 La base de données source peut également être renommée lors du processus de transfert. Si vous voulez transférer une base de données vers une instance de destination de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contenant déjà une base de données portant le même nom, le changement de nom de la base de données source permet le transfert de cette base de données. Cependant, les noms de fichiers de base de données doivent également être différents. Si des fichiers de base de données portant le même nom existent déjà sur la destination, la tâche échoue.  
  
 Lorsque vous copiez une base de données, sa taille ne peut pas être inférieure à la taille de la base de données **model** sur le serveur de destination. Vous pouvez soit augmenter la taille de la base de données à copier, soit réduire la taille de la base de données **model**.  
  
 À l'exécution, la tâche de transfert de base de données se connecte aux serveurs source et destination en utilisant un ou deux gestionnaires de connexions SMO. Lorsque vous créez une copie de base de données sur le même serveur, un seul gestionnaire de connexions SMO est requis. Les gestionnaires de connexions SMO sont configurés indépendamment de la tâche de transfert de bases de données, puis sont référencés dans cette tâche. Les gestionnaires de connexions SMO spécifient le serveur et le mode d'authentification à utiliser lorsque la tâche accède au serveur. Pour plus d'informations, consultez [SMO Connection Manager](../connection-manager/smo-connection-manager.md).  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de tâche de transfert de bases de données &#40;page Général&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Éditeur de tâche de transfert de bases de données &#40;page Bases de données&#41;](../transfer-database-task-editor-databases-page.md)  
  
-   [Page Expressions](../expressions/expressions-page.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-transfer-database-task"></a>Configuration par programmation de la tâche de transfert de bases de données  
 Pour plus d'informations sur la définition par programme de ces propriétés, cliquez sur la rubrique suivante :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferDatabaseTask.TransferDatabaseTask>  
  
  
