---
title: Traitement à distance (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d58bcb3c-0b3f-4ab0-81eb-4fdcc86153af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 699cc312b2f4b0a716d08259daf189276551e5d4
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545768"
---
# <a name="remote-processing-analysis-services"></a>Traitement à distance (Analysis Services)
  Vous pouvez exécuter un traitement planifié ou sans assistance sur une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . La demande de traitement proviendra d'un ordinateur, mais s'exécutera sur un autre ordinateur du même réseau.  
  
## <a name="prerequisites"></a>Prérequis  
  
-   Si vous exécutez différentes versions de SQL Server sur chaque ordinateur, les bibliothèques clientes doivent correspondre à la version de l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui traite le modèle. Par exemple, si le traitement se trouve sur une instance [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] , l'ordinateur d'où provient la demande doit disposer de la bibliothèque cliente correspondant à [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]. Consultez [Fournisseurs de données utilisés pour les connexions Analysis Services](../instances/data-providers-used-for-analysis-services-connections.md).  
  
-   Sur le serveur distant, l'option **Autoriser les connexions à distance à cet ordinateur** doit être activée, et le compte qui émet la demande de traitement doit être répertorié en tant qu'utilisateur autorisé.  
  
-   Les règles du Pare-feu Windows doivent être configurées pour autoriser les connexions entrantes à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Vérifiez que vous pouvez vous connecter à l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distante à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Consultez [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
-   Résolvez les erreurs de traitement local existantes avant de tenter le traitement à distance. Quand le traitement de la demande est local, vérifiez que les données peuvent être récupérées à partir de la source de données relationnelles externe. Pour obtenir des instructions sur la spécification des informations d’identification utilisées pour récupérer des données, consultez [Définir les options d’emprunt d’identité &#40;SSAS - Multidimensionnel&#41;](set-impersonation-options-ssas-multidimensional.md).  
  
## <a name="on-demand-remote-processing"></a>Traitement à distance à la demande  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] accepte les demandes de traitement des comptes d'utilisateur ou d'application disposants des autorisations d'administrateur pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Si vous êtes administrateur, vérifiez que vous pouvez vous connecter à l'instance distante et traiter la base de données manuellement via la connexion à distance.  
  
1.  Sur l'ordinateur qui sera utilisé pour planifier le traitement, démarrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , puis connectez-vous à l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distante.  
  
2.  Cliquez avec le bouton droit sur la base de données, sélectionnez **Traiter**, pointez sur **Script** , puis choisissez **Action de script dans une nouvelle fenêtre de requête**. Les commandes utilisées pour appeler le traitement apparaîtront dans la fenêtre de requête.  
  
3.  Cliquez sur **OK** pour commencer le traitement.  
  
     Si cette tâche se termine correctement, vous obtiendrez une requête XMLA que vous pourrez incorporer dans une tâche planifiée. Par ailleurs, si la tâche se termine correctement, cela confirme qu'il n'existe aucun problème de connexion.  
  
## <a name="schedule-remote-processing-using-sql-server-agent-service"></a>Planifier le traitement à distance à l'aide du service SQL Server Agent  
 Par défaut, le service SQL Server Agent s'exécute sous un compte virtuel, avec des connexions réseau établies avec le compte d'ordinateur. Pour éviter d'avoir à accorder des droits d'administration à un compte d'ordinateur sur l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distante, vous devez modifier le compte du service SQL Server Agent pour qu'il soit s'exécuté en tant que compte d'utilisateur de domaine doté de privilèges minimum.  
  
 Veillez à accorder toutes les autorisations nécessaires, notamment en attribuant au compte **sysadmin** les droits sur l'instance du moteur de base de données qui fournit le service.  
  
 Utilisez les liens suivants pour définir les autorisations :  
  
-   [Configurer l'Agent SQL Server](../../ssms/agent/configure-sql-server-agent.md)  
  
-   [SQL Server Agent Components](../../ssms/agent/sql-server-agent.md#Components) suggère d'autres rôles serveur fixes s'il n'est pas possible d'accorder des autorisations à **sysadmin** .  
  
 Après avoir configuré les autorisations du compte, passez aux étapes suivantes.  
  
#### <a name="grant-the-sql-server-agent-account-administrator-permission-on-ssas"></a>Accorder des droits d'administration au compte SQL Server Agent sur SSAS  
  
1.  À l'aide de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], connectez-vous à l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distante.  
  
2.  Cliquez avec le bouton droit sur le nom du serveur, puis cliquez sur**Propriétés**et sur **Sécurité**.  
  
3.  Cliquez sur **Ajouter** pour ajouter le compte SQL Server Agent.  
  
#### <a name="create-the-job"></a>Créer un travail  
  
1.  Dans Management Studio, connectez-vous à l'instance locale du moteur de base de données. SQL Server Agent est le dernier élément dans l'Explorateur d'objets. Si nécessaire, démarrez le service.  
  
2.  Cliquez avec le bouton droit sur **Travaux**, cliquez sur **Nouveau travail** , puis entrez un nom.  
  
3.  Dans Étapes, cliquez sur **Nouveau** , puis entrez un nom.  
  
4.  Dans Type, sélectionnez **Commande SQL Server Analysis Services**.  
  
5.  Dans Serveur, entrez le nom de l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distante.  
  
6.  Dans Commande, collez la commande XMLA pour le traitement de la base de données. Il s'agit du script XMLA que vous avez généré à l'étape de vérification pour le traitement à distance à la demande. Cliquez sur **OK** pour enregistrer le travail.  
  
#### <a name="start-sql-server-profiler"></a>Démarrer SQL Server Profiler  
  
1.  Sur l'ordinateur distant, démarrez SQL Server Profiler. Connectez-vous à l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , puis cliquez sur **Exécuter** pour démarrer la trace à l'aide des événements par défaut.  
  
     Vous allez utiliser SQL Server Profiler pour surveiller les événements de traitement à mesure qu'ils se produisent.  
  
2.  Si vous le souhaitez, vous pouvez définir des propriétés de trace pour envoyer la trace vers un fichier ou une table dans une base de données.  
  
#### <a name="run-the-job"></a>Exécuter le travail  
  
1.  Sur l'ordinateur utilisé pour exécuter le travail, vérifiez que le travail peut effectuer l'opération de base. Dans l’Explorateur d’objets, sous SQL Server Agent, développez **Travaux**, cliquez avec le bouton droit sur le travail que vous venez de créer, puis cliquez sur **Démarrer le travail à l’étape**. Le travail démarre immédiatement. Vous pouvez surveiller la progression dans SQL Server Profiler.  
  
2.  Dans la dernière étape, modifiez le travail pour qu'il soit exécuté selon la planification de votre choix, en ajoutant toutes les alertes ou notifications nécessaires à la gestion du travail. Vous pouvez également affiner le script de traitement ou créer plusieurs étapes au sein du travail pour traiter les objets indépendamment.  
  
## <a name="see-also"></a>Voir aussi  
 [Composants SQL Server Agent](../../ssms/agent/sql-server-agent.md#Components)   
 [Planifier des tâches administratives SSAS avec SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md)   
 [Traitement par lots &#40;Analysis Services&#41;](batch-processing-analysis-services.md)   
 [Traitement d’objets de modèle multidimensionnel](processing-a-multidimensional-model-analysis-services.md)   
 [Traitement d’objets &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)  
  
  
