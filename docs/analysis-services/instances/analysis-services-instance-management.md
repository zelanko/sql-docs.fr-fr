---
title: SQL Server Analysis Services de gestion de serveur | Microsoft Docs
ms.date: 11/15/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 10623ea2c0dcb413bad08e1d68dfd9d5c9a9984a
ms.sourcegitcommit: c3b190f8f87a4c80bc9126bb244896197a6dc453
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56852884"
---
# <a name="sql-server-analysis-services-server-management"></a>Gestion de serveur SQL Server Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

Pour Azure Analysis Services, consultez [gérer Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-manage).

## <a name="instances"></a>Instances

  Une instance de serveur d’Analysis Services est une copie de la **msmdsrv.exe** exécutable qui s’exécute comme un service de système d’exploitation. Chaque instance est entièrement indépendante des autres instances situées sur le même serveur et dispose de ses propres paramètres de configuration, autorisations, ports, comptes de démarrage, stockage de fichier, et propriétés de mode serveur.  
  
 Chaque instance s’exécute en tant que service Windows, Msmdsrv.exe, dans le contexte de sécurité d’un compte d’ouverture de session défini.  
  
-   Le nom du service de l’instance par défaut est MSSQLServerOLAPService.  
  
-   Le nom de service de chaque instance nommée d’est MSOLAP$ InstanceName.  
  
> [!NOTE]  
>  Si plusieurs instances sont installés, le programme d’installation installe également un service redirecteur, qui est intégré à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service Browser. Le service redirecteur est chargé de diriger les clients vers les instances nommées appropriées [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser s'exécute toujours dans le contexte de sécurité du compte de service local, un compte d'utilisateur limité utilisé par Windows pour les services système qui n'accèdent pas aux ressources en dehors de l'ordinateur local.  
  
 La notion d'instances multiples signifie que vous pouvez monter en puissance en installant plusieurs instances de serveur sur le même matériel. Pour Analysis Services en particulier, cela signifie également que vous pouvez prendre en charge différents modes serveur en disposant de plusieurs instances sur le même serveur, chacune étant configurée pour s'exécuter dans un mode spécifique.  

## <a name="server-mode"></a>Mode serveur
  
 Le mode serveur est une propriété de serveur qui détermine l'architecture de stockage et de mémoire utilisée pour cette instance. Un serveur qui s'exécute en mode multidimensionnel utilise la couche de gestion des ressources créée pour les bases de données de cube multidimensionnelles et les modèles d'exploration de données. Par opposition, le mode serveur tabulaire utilise le moteur d’analyse en mémoire VertiPaq et la compression de données pour agréger les données selon la requête.  
  
 Les différences entre l'architecture de stockage et de mémoire impliquent qu'une instance d'Analysis Services peut exécuter des bases de données tabulaires ou des bases de données multidimensionnelles, mais pas les deux. La propriété du mode serveur détermine le type de base de données qui s'exécute sur l'instance.  
  
 Le mode serveur est défini pendant l'installation lorsque vous spécifiez le type de base de données qui s'exécutera sur le serveur. Pour prendre en charge tous les modes disponibles, vous pouvez installer plusieurs instances d'Analysis Services, chacune étant déployée dans un mode serveur qui correspond aux projets que vous créez.  
  
 En règle générale, la plupart des tâches d'administration que vous devez effectuer ne varient pas au niveau du mode. En tant qu'administrateur système d'Analysis Services, vous pouvez utiliser les mêmes procédures et scripts pour gérer une instance d'Analysis Services sur votre réseau, quelle que soit la manière dont elle a été installée.  
  
> [!NOTE]  
>  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint constitue toutefois une exception. L’administration de serveur d’un déploiement [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] s’effectue toujours dans le contexte d’une batterie de serveurs SharePoint. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] diffère des autres modes serveur en ceci qu’il est toujours à instance unique et est toujours géré à l’aide de l’Administration centrale de SharePoint ou de l’outil de configuration de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Bien qu’il soit possible de se connecter à [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint dans SQL Server Management Studio ou [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cette méthode est déconseillée. Une batterie de serveurs SharePoint inclut l'infrastructure qui synchronise l'état du serveur et surveille la disponibilité du serveur. L'utilisation d'autres outils peut interférer avec ces opérations. Pour plus d’informations sur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] administration de serveur, consultez [Power Pivot pour SharePoint ](../../analysis-services/power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md).  
  
  
  
## <a name="see-also"></a>Voir aussi  
 [Comparaison des Solutions tabulaires et multidimensionnelles ](../../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
 [Déterminer le mode serveur d'une instance Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
