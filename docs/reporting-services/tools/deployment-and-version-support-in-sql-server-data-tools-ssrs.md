---
title: "Déploiement et prise en charge de la Version de SQL Server Data Tools (SSDT) | Documents Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36f5686d-7e40-4f31-be81-bd197ca33a02
caps.latest.revision: 19
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 60272ce672c0a32738b0084ea86f8907ec7fc0a5
ms.openlocfilehash: 173d2a355d1084b22bdc90643484dbab2568e0b0
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---
# <a name="deployment-and-version-support-in-sql-server-data-tools-ssdt"></a>Déploiement et prise en charge de la Version de SQL Server Data Tools (SSDT)
  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] prend en charge les scénarios suivants :  
  
-   Ouvrez les définitions de rapport (*.rdl) et les projets de serveurs de rapports (\*.rptproj).  
  
-   Créez les définitions de rapport.  
  
-   Affichez un aperçu des rapports dans le Concepteur de rapports.  
  
-   Déployez les rapports sur le serveur de rapports.  
  
##  <a name="bkmk_ConfigurationandDeploymentProperties"></a> Propriétés de configuration et de déploiement  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] prend en charge les configurations de projet. Une configuration de projet consiste en un ensemble de propriétés qui spécifient des emplacements et des comportements lorsqu'un projet est généré dans le cadre de l'aperçu ou du déploiement de rapports. Pour en savoir plus sur les configurations de projet, consultez la documentation Visual Studio.  
  
 Utilisez les configurations de projet pour contrôler la mise à niveau des définitions de rapport aux versions de schéma compatibles avec les serveurs de rapports cibles. Les propriétés contrôlées par les configurations de projet incluent le serveur de rapports cible, le dossier où le processus de génération stocke temporairement les définitions de rapport pour l'aperçu et le déploiement, et les niveaux d'erreur.  
  
 Les rapports sont générés avant d'être restitués comme aperçus dans le Concepteur de rapports ou déployés vers le serveur de rapports.  
  
 Définissez les propriétés de configuration dans la boîte de dialogue [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] **Propriété du projet** .  
  
 Les propriétés de déploiement et de génération sont les suivantes :  
  
-   OutputPath est une propriété de génération qui identifie le chemin des dossiers où stocker la définition de rapport utilisée dans la vérification de la génération, le déploiement et l’aperçu de rapports.  
  
-   ErrorLevel est une propriété de génération qui identifie la gravité des problèmes de génération signalés comme erreurs. Les problèmes avec des niveaux de gravité inférieurs ou égaux à la valeur de ErrorLevel sont signalés comme erreurs ; sinon, les problèmes sont signalés comme avertissements. Pour plus d’informations, consultez la section « Validation rapport et niveaux d’erreur » [concevoir des rapports avec le Concepteur de rapports &#40; SSRS &#41; ](../../reporting-services/tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).  
  
-   TargetServerVersion est une propriété de déploiement qui identifie la version attendue de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installée sur le serveur de rapports cible spécifié dans la propriété TargetServerURL.  
  
 Lorsque vous spécifiez la version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans la boîte de dialogue **Propriété du projet** , les rapports ne sont pas rétablis automatiquement à la version antérieure. De ce fait, un projet Report Server peut contenir des rapports des deux versions différentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Quand le projet Report Server est déployé, tous les rapports du projet sont convertis dans la version spécifiée dans TargetServerVersion.  
  
 Vous pouvez ajouter plusieurs configurations de projet à un projet ; chacune est utilisée pour un scénario différent, tel que le déploiement vers différentes versions de serveurs de rapports. Pour plus d’informations, consultez [Définir des propriétés de déploiement &#40;Reporting Services&#41;](../../reporting-services/tools/set-deployment-properties-reporting-services.md) et [Pages de propriétés du projet, boîte de dialogue ](../../reporting-services/tools/project-property-pages-dialog-box.md).  
  
##  <a name="bkmk_SupportedVersions"></a> Versions prises en charge  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], l’environnement de développement 32 bits pour les projets du serveur de rapports, n’est pas conçu pour s’exécuter sur [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)]-ordinateurs et n’est pas installé sur [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)]-serveurs. Une prise en charge de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] est en revanche possible sur des ordinateurs x64.  
  
 Le tableau suivant décrit les versions prises en charge pour la création et la publication de rapports dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
> [!NOTE]  
>  Le schéma n'a pas changé depuis [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
|Type de projet ou de fichier|Version|Création de rapports|Publier des rapports|Remarques|  
|--------------------------|-------------|--------------------|---------------------|-----------|  
|Projet Report Server<br /><br /> ou<br /><br /> Assistant Projet Report Server|[!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]|Schéma RDL 2016|[!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]||  
|Projet Report Server<br /><br /> ou<br /><br /> Assistant Projet Report Server|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|Schéma RDL 2014|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]||  
|Projet Report Server<br /><br /> ou<br /><br /> Assistant Projet Report Server|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|Schéma RDL 2012|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]||  
|Projet Report Server<br /><br /> ou<br /><br /> Assistant Projet Report Server|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|2008 R2 RDL (schéma)|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]||  
|Projet Report Server<br /><br /> ou<br /><br /> Assistant Projet Report Server|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|Schéma RDL 2008|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] uniquement|Permet une mise à niveau locale de schémas RDL (Report Definition Language) 2003, 2005 et 2008.|  
  
 Pour plus d’informations sur l’ouverture de rapports dans une version précédente du schéma de définition de rapport, consultez [Mettre à niveau des rapports](../../reporting-services/install-windows/upgrade-reports.md). Pour plus d'informations sur des schémas de définition de rapport spécifiques, consultez la rubrique consacrée à la [spécification RDL (Report Definition Language)](http://go.microsoft.com/fwlink/?linkid=116865).  
  
## <a name="see-also"></a>Voir aussi  
 [Publication des sources de données et des rapports](../../reporting-services/reports/publishing-data-sources-and-reports.md)  
  
  

