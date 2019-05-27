---
title: Gestion de l’Instance Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0455fa4f-b92d-4a8b-a8f0-f2a268a5c84e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ac0c6637dd08dc2ea8927853b7a6bf8dccca454d
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66080349"
---
# <a name="analysis-services-instance-management"></a>Gestion d'instances Analysis Services
  Une instance d'Analysis Services est une copie de l'exécutable `msmdsrv.exe` qui s'exécute en tant que service du système d'exploitation. Chaque instance est entièrement indépendante des autres instances situées sur le même serveur et dispose de ses propres paramètres de configuration, autorisations, ports, comptes de démarrage, stockage de fichier, et propriétés de mode serveur.  
  
 Chaque instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] exécute un service Windows, Msmdsrv.exe, dans le contexte de sécurité d'un compte d'ouverture de session défini.  
  
-   Le nom de service d'une instance par défaut [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est MSSQLServerOLAPService.  
  
-   Le nom de service de chaque instance nommée [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est MSOLAP$InstanceName.  
  
> [!NOTE]  
>  Si plusieurs instances de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sont installées, le programme d'installation installe également un service redirecteur intégré au service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser. Le service redirecteur est chargé de diriger les clients vers les instances nommées appropriées [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser s'exécute toujours dans le contexte de sécurité du compte de service local, un compte d'utilisateur limité utilisé par Windows pour les services système qui n'accèdent pas aux ressources en dehors de l'ordinateur local.  
  
 La notion d'instances multiples signifie que vous pouvez monter en puissance en installant plusieurs instances de serveur sur le même matériel. Pour Analysis Services en particulier, cela signifie également que vous pouvez prendre en charge différents modes serveur en disposant de plusieurs instances sur le même serveur, chacune étant configurée pour s'exécuter dans un mode spécifique.  
  
 Le mode serveur est une propriété de serveur qui détermine l'architecture de stockage et de mémoire utilisée pour cette instance. Un serveur qui s'exécute en mode multidimensionnel utilise la couche de gestion des ressources créée pour les bases de données de cube multidimensionnelles et les modèles d'exploration de données. Par opposition, le mode serveur tabulaire utilise le moteur d'analyse en mémoire xVelocity (VertiPaq) et la compression de données pour agréger les données selon la requête.  
  
 Les différences entre l'architecture de stockage et de mémoire impliquent qu'une instance d'Analysis Services peut exécuter des bases de données tabulaires ou des bases de données multidimensionnelles, mais pas les deux. La propriété du mode serveur détermine le type de base de données qui s'exécute sur l'instance.  
  
 Le mode serveur est défini pendant l'installation lorsque vous spécifiez le type de base de données qui s'exécutera sur le serveur. Pour prendre en charge tous les modes disponibles, vous pouvez installer plusieurs instances d'Analysis Services, chacune étant déployée dans un mode serveur qui correspond aux projets que vous créez.  
  
 En règle générale, la plupart des tâches d'administration que vous devez effectuer ne varient pas au niveau du mode. En tant qu'administrateur système d'Analysis Services, vous pouvez utiliser les mêmes procédures et scripts pour gérer une instance d'Analysis Services sur votre réseau, quelle que soit la manière dont elle a été installée.  
  
> [!NOTE]  
>  PowerPivot pour SharePoint constitue toutefois une exception. L'administration de serveur d'un déploiement PowerPivot s'effectue toujours dans le contexte d'une batterie de serveurs SharePoint. PowerPivot diffère des autres modes serveur en ceci qu'il est toujours à instance unique et est toujours géré via l'Administration centrale de SharePoint ou l'outil de configuration de PowerPivot. Bien qu'il soit possible de se connecter à PowerPivot pour SharePoint dans SQL Server Management Studio ou [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cette méthode est déconseillée. Une batterie de serveurs SharePoint inclut l'infrastructure qui synchronise l'état du serveur et surveille la disponibilité du serveur. L'utilisation d'autres outils peut interférer avec ces opérations. Pour plus d’informations sur l’administration de serveur PowerPivot, consultez [PowerPivot pour SharePoint &#40;SSAS&#41;](../power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Lien|Description de la tâche|  
|----------|----------------------|  
|[Configuration consécutive à l’installation &#40;Analysis Services&#41;](post-install-configuration-analysis-services.md)|Décrit les tâches obligatoires et facultatives qui complètent ou modifient une installation d'Analysis.|  
|[Se connecter à Analysis Services](connect-to-analysis-services.md)|Décrit les propriétés des chaînes de connexion, les bibliothèques clientes, les méthodologies d'authentification, ainsi que les étapes requises pour établir ou désactiver des connexions.|  
|[Analyser une instance Analysis Services](monitor-an-analysis-services-instance.md)|Décrit les outils et techniques permettant de surveiller une instance de serveur, notamment l'utilisation de l'Analyseur de performances et de SQL Server Profiler.|  
|[Tâches d'administration à l'aide de scripts dans Analysis Services](../script-administrative-tasks-in-analysis-services.md)|Explique comment automatiser de nombreuses tâches d'administration, notamment le traitement.|  
|[Scénarios de globalisation pour données multidimensionnelles Analysis Services](../globalization-scenarios-for-analysis-services-multiidimensional.md)|Explique la prise en charge linguistique et du classement, décrit les étapes permettant de modifier les deux propriétés et fournit des conseils pour définir et tester les comportements de langue et de classement.|  
|[Enregistrer les opérations dans Analysis Services](log-operations-in-analysis-services.md)|Décrit les journaux et explique comment les configurer.|  
  
## <a name="see-also"></a>Voir aussi  
 [Comparaison des solutions tabulaires et multidimensionnelles &#40;SSAS&#41;](../comparing-tabular-and-multidimensional-solutions-ssas.md)   
 [Outils de Configuration de PowerPivot](../power-pivot-sharepoint/power-pivot-configuration-tools.md)   
 [Administration de serveur PowerPivot et de Configuration dans l’Administration centrale](../power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Déterminer le mode serveur d'une instance Analysis Services](determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
