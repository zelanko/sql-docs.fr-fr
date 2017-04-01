---
title: "Accorder des droits d’administrateur de serveur &#224; une instance Analysis Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "droits d'administrateur [Analysis Services]"
  - "autorisations d'administration sur l'ensemble du serveur [Analysis Services]"
ms.assetid: 20d1234b-a457-4a84-ae08-fe356870c466
caps.latest.revision: 37
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 37
---
# Accorder des droits d’administrateur de serveur &#224; une instance Analysis Services
  Les membres du rôle administrateur de serveur dans une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ont un accès illimité à tous les objets et données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de cette instance. Un utilisateur doit être membre du rôle administrateur de serveur pour pouvoir exécuter n'importe quelle tâche sur le serveur, telle que créer ou traiter une base de données, modifier des propriétés du serveur ou lancer une trace (autre que pour les événements de traitement).  
  
 L'appartenance au rôle est établie lorsque [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est installé. L’utilisateur exécutant le programme d’installation peut s’ajouter lui-même au rôle, ou ajouter un autre utilisateur. Vous devez spécifier au moins un administrateur avant que le programme d’installation vous autorise à poursuivre.  
  
 Par défaut, des droits d'administration sont également accordés aux membres du groupe local Administrateurs dans Analysis Server. Bien que l'appartenance au rôle administrateur de serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne soit pas accordée explicitement au groupe local, les administrateurs locaux peuvent créer des bases de données, ajouter des utilisateurs et des autorisations et effectuer toute autre tâche autorisée aux administrateurs système. L’octroi implicite d’autorisations d’administrateur est configurable. Il est déterminé par la propriété de serveur **BuiltinAdminsAreServerAdmins** , qui a la valeur **true** par défaut. Vous pouvez modifier cette propriété dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour plus d’informations, voir [Security Properties](../../analysis-services/server-properties/security-properties.md).  
  
 Après l’installation, vous pouvez modifier l’appartenance aux rôles pour ajouter d’autres utilisateurs qui nécessitent des droits d’accès complets au service. Vous pouvez également gérer les rôles de serveur en utilisant AMO (Analysis Management Objects). Pour plus d’informations, consultez [Développement avec AMO &#40;Analysis Management Objects&#41;](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] offre une série de rôles de plus en plus granulaires pour le traitement et l’exécution de requêtes aux niveaux serveur, base de données et objet. Pour obtenir des instructions sur l’utilisation de ces rôles, consultez [Rôles et autorisations &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md).  
  
## Modifier l'appartenance au rôle de serveur  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à l’instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], cliquez avec le bouton droit sur le nom de l’instance dans l’Explorateur d’objets, puis sélectionnez **Propriétés**.  
  
2.  Cliquez sur **Sécurité** dans le volet **Sélectionner une page** , puis sur **Ajouter** au bas de la page pour ajouter un ou plusieurs utilisateurs ou groupes Windows au rôle de serveur.  
  
     ![Boîte de dialogue Ajouter des utilisateurs dans management studio](../../analysis-services/instances/media/ssas-serveradminadd.png "Boîte de dialogue Ajouter des utilisateurs dans management studio")  
  
### Ajouter des comptes d’ordinateur  
 Vous pouvez également utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour définir un compte d’ordinateur en tant que membre du groupe d’administrateurs [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
1.  Dans la boîte de dialogue **Sélectionner des utilisateurs ou des groupes** , cliquez sur **Emplacements**.  
  
2.  Sélectionnez le domaine auquel appartiennent les ordinateurs que vous souhaitez ajouter, ou sélectionnez **Tout l’annuaire** et cliquez sur **OK**.  
  
3.  Cliquez sur **Types d'objets**.  
  
4.  Sélectionnez **Ordinateurs** , puis cliquez sur **OK**.  
  
     ![add computer accounts as ssas administrators](../../analysis-services/instances/media/ssas-in-ssms-computerobjects.png "add computer accounts as ssas administrators")  
  
5.  Dans la zone de texte **Entrez les noms d’objets à sélectionner** , tapez le nom de l’ordinateur et cliquez sur **Vérifier les noms** pour vous assurer que le compte d’ordinateur se trouve aux emplacements actuels. Si le compte d’ordinateur est introuvable, vérifiez le nom d’ordinateur et le domaine dont l’ordinateur est membre.  
  
## Compte Service NT\SSASTelemetry  
 **Service NT/SSASTelemetry** est un compte d’ordinateur à faibles privilèges créé pendant l’installation et utilisé exclusivement pour exécuter l’implémentation [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] du service Programme d’amélioration de l’expérience utilisateur. Ce service requiert des droits d’administrateur sur l’instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour exécuter plusieurs commandes de détection. Pour plus d'informations, consultez [Customer Experience Improvement Program for SQL Server Data Tools](../../sql-server/customer-experience-improvement-program-for-sql-server-data-tools.md) et [Microsoft SQL Server Privacy Statement](../Topic/Microsoft%20SQL%20Server%20Privacy%20Statement.md) .  
  
## Voir aussi  
 [Autorisation de l’accès à des objets et des opérations &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)   
 [Rôles de sécurité &#40;Analysis Services - Données multidimensionnelles&#41;](../../analysis-services/multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)  
  
  