---
title: Transfert d’objets SQL Server, tâche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfersqlserverobjectstask.f1
helpviewer_keywords:
- Transfer SQL Server Objects task [Integration Services]
ms.assetid: fe86d6e5-e415-406c-88f3-dc3ef71bd5f0
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 01b985a1bb818e7b3d3612596bb4e2b7fa6fd393
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829462"
---
# <a name="transfer-sql-server-objects-task"></a>Tâche de transfert d'objets SQL Server
  La tâche de transfert d’objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transfère un ou plusieurs types d’objets d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entre des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par exemple, la tâche peut copier des tables et des procédures stockées. Selon la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisée comme source, différents types d’objets sont disponibles pour la copie. Par exemple, seule une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inclut des schémas et des agrégats définis par l’utilisateur.  
  
## <a name="objects-to-transfer"></a>Objets à transférer  
 Les rôles de serveur, les rôles et les utilisateurs de la base de données spécifiée peuvent être copiés, ainsi que les autorisations pour les objets transférés. En copiant les utilisateurs, les rôles et les autorisations associés avec les objets, les objets transférés peuvent être opérationnels immédiatement sur le serveur de destination.  
  
 Le tableau suivant présente la liste des types d'objets qui peuvent être copiés.  
  
|Object|  
|------------|  
|Tables|  
|Affichages|  
|Procédures stockées|  
|Fonctions définies par l'utilisateur|  
|Valeurs par défaut|  
|Types de données définis par l’utilisateur|  
|Fonctions de partition|  
|Schémas de partition|  
|Schémas|  
|Assemblys|  
|Agrégats définis par l'utilisateur|  
|Types définis par l'utilisateur|  
|Collection de schémas XML|  
  
 Les types définis par l'utilisateur (UDT) qui ont été créés dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possèdent des dépendances avec les assemblys CLR (Common Language Runtime). Si vous utilisez la tâche de transfert d'objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour transférer des types UDT, vous devez également configurer la tâche de transfert d'objets dépendants. Pour transférer des objets dépendants, affectez à la propriété `IncludeDependentObjects` la valeur `True`.  
  
### <a name="table-options"></a>Options des tables  
 Lors de la copie de tables, vous pouvez indiquer les types des éléments associés aux tables à inclure dans le processus de copie. Les types d'éléments suivants peuvent être copiés avec la table associée :  
  
-   Index  
  
-   Déclencheurs  
  
-   Index de texte intégral  
  
-   Clés primaires  
  
-   Clés étrangères  
  
 Vous pouvez également indiquer si le script généré par la tâche est au format Unicode.  
  
## <a name="destination-options"></a>Options de destination  
 Vous pouvez configurer la tâche de transfert d'objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour qu'elle inclue des noms de schéma, des données, des propriétés étendues d'objets transférés et des objets dépendants dans le transfert. Si des données sont copiées, la tâche peut remplacer les données existantes ou les conserver.  
  
 Certaines options ne s'appliquent qu'à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par exemple, seul [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge les schémas.  
  
## <a name="security-options"></a>Options de sécurité  
 La tâche de transfert d’objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut inclure des utilisateurs et rôles au niveau de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la source, des connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ainsi que les autorisations pour les objets transférés. Par exemple, le transfert peut inclure les autorisations sur les tables transférées.  
  
## <a name="transfer-objects-between-instances-of-sql-server"></a>Transférer des objets entre des instances de SQL Server  
 La tâche de transfert d'objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge une source et une destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="events"></a>Événements  
 La tâche génère un événement d'information qui indique l'objet transféré et un événement d'avertissement lorsque qu'un objet est remplacé. Un événement d'information est également généré pour les actions telles que la troncation des tables de base de données.  
  
 La tâche de transfert d’objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’indique pas les stades intermédiaires de l’avancement du transfert des objets : elle signale uniquement la tâche comme réalisée à 0 % ou à 100 %.  
  
## <a name="execution-value"></a>Valeur d'exécution  
 La valeur d'exécution, stockée dans la propriété `ExecutionValue` de la tâche, retourne le nombre d'objets transférés. En affectant une variable définie par l'utilisateur à la propriété `ExecValueVariable` de la tâche de transfert d'objets SQL Server, les informations sur le transfert d'objets peuvent être mises à la disposition d'autres objets du package. Pour plus d’informations, consultez [Variables Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md) et [Utiliser des variables dans des packages](../use-variables-in-packages.md).  
  
## <a name="log-entries"></a>Entrées du journal  
 La tâche de transfert d'objets SQL Server comporte les entrées de journal personnalisées suivantes :  
  
-   TransferSqlServerObjectsTaskStartTransferringObjects   Cette entrée du journal indique que le transfert a commencé. L'entrée du journal inclut l'heure de début.  
  
-   TransferSqlServerObjectsTaskFinishedTransferringObjects   Cette entrée du journal indique que le transfert est terminé. L'entrée du journal inclut l'heure de fin.  
  
 En outre, une entrée de journal pour l'événement `OnInformation` indique le nombre d'objets pour les types d'objet qui ont été sélectionnés pour le transfert, le nombre d'objets transférés, ainsi que les actions telles que la troncation de tables lorsque des données sont transférées avec les tables. Une entrée de journal pour l'événement `OnWarning` est écrite pour chaque objet de destination remplacé.  
  
## <a name="security-and-permissions"></a>Sécurité et autorisations  
 L'utilisateur doit avoir l'autorisation de parcourir les objets sur le serveur source et de supprimer ou de créer des objets sur le serveur de destination. L'utilisateur doit en outre avoir accès à la base de données spécifiée et aux objets de base de données.  
  
## <a name="configuration-of-the-transfer-sql-server-objects-task"></a>Configuration de la tâche de transfert d'objets SQL Server  
 La tâche de transfert d'objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être configurée pour transférer tous les objets, tous les objets d'un certain type, ou seulement les objets spécifiés d'un type. Par exemple, vous pouvez choisir de ne copier que les tables sélectionnées dans la base de données AdventureWorks.  
  
 Si la tâche de transfert d’objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transfère des tables, vous pouvez spécifier les types des objets associés aux tables à copier avec les tables. Par exemple, vous pouvez spécifier que les clés primaires sont copiées avec les tables.  
  
 Pour améliorer la fonctionnalité des objets transférés, vous pouvez configurer la tâche de transfert d'objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour qu'elle inclue des noms de schéma, des données, des propriétés étendues d'objets transférés et des objets dépendants dans le transfert. Lors de la copie de données, vous pouvez spécifier s'il faut remplacer ou ajouter les données existantes.  
  
 À l’exécution, la tâche de transfert d’objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se connecte aux serveurs source et de destination en utilisant deux gestionnaires de connexions SMO. Les gestionnaires de connexions SMO sont configurés indépendamment de la tâche de transfert d’objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , puis référencés dans la tâche de transfert d’objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les gestionnaires de connexions SMO spécifient le serveur et le mode d'authentification à utiliser lors de l'accès au serveur. Pour plus d'informations, consultez [SMO Connection Manager](../connection-manager/smo-connection-manager.md).  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de tâche de transfert d’objets SQL Server &#40;page Général&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Éditeur de tâche de transfert d’objets SQL Server &#40;page Objets&#41;](../transfer-sql-server-objects-task-editor-objects-page.md)  
  
-   [Page Expressions](../expressions/expressions-page.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-transfer-sql-server-objects-task"></a>Configuration par programmation de la tâche de transfert d'objets SQL Server  
 Pour plus d'informations sur la définition par programme de ces propriétés, cliquez sur la rubrique suivante :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferSqlServerObjectsTask.TransferSqlServerObjectsTask>  
  
  
