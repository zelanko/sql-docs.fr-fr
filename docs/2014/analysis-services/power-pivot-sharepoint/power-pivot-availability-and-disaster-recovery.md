---
title: Disponibilité et récupération d’urgence PowerPivot (SQL Server 2014) | Microsoft Docs
ms.custom: ''
ms.date: 03/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4aaf008c-3bcb-4dbf-862c-65747d1a668c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bf560d489a1631e31f470134d497d3d897f6f35e
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78175678"
---
# <a name="powerpivot-availability-and-disaster-recovery-sql-server-2014"></a>Récupération d'urgence et disponibilité de PowerPivot (SQL Server 2014)
  La disponibilité et les plans de récupération d'urgence pour [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] dépendent principalement de la conception de votre batterie de serveurs SharePoint, de la durée de temps mort acceptable pour les différents composants, ainsi que des outils et des meilleures pratiques que vous implémentez pour la disponibilité SharePoint. Cette rubrique résume les technologies et contient des exemples de diagrammes de topologie à prendre en compte lors de la planification [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] de la disponibilité et de la récupération d’urgence pour un déploiement.

||
|-|
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|

 **Dans cette rubrique :**

-   [Exemple de topologie SharePoint 2013 pour une haute disponibilité de PowerPivot](#bkmk_sharepoint2013)

-   [Exemple de topologie SharePoint 2010 pour une haute disponibilité de PowerPivot](#bkmk_sharepoint2010)

-   [Base de données d’application de service PowerPivot et technologies de disponibilité et de récupération de SQL Server](#bkmk_sql_server_technologies)

-   [Liens vers des informations supplémentaires](#bkmk_more_resources)

##  <a name="bkmk_sharepoint2013"></a>Exemple de topologie SharePoint 2013 pour la haute disponibilité PowerPivot
 Dans un déploiement [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013, il existe davantage de souplesse dans la façon dont vous concevez la disponibilité de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Dans SharePoint 2013, l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] déployée en mode SharePoint, également appelée serveur [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] , s'exécute en dehors de la batterie de serveurs SharePoint et peut être installée sur des serveurs distincts. Chaque instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint est inscrite avec Excel Services. Le service partagé [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] et l'application de service s'exécutent sur des serveurs d'applications SharePoint.

 Le schéma suivant illustre un exemple de déploiement [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013. Cet exemple prend en charge une bonne disponibilité des services [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] et suppose une sauvegarde régulière des bases de données.

 ![disponibilité powerpivot dans 2013](../media/ssas-powerpivot-services-2013.png "disponibilité powerpivot dans 2013")

-   **(1)** les serveurs Web frontaux. Utilisez le complément [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 pour installer les fournisseurs de données sur chaque serveur. Pour plus d’informations, consultez [installer ou désinstaller le complément PowerPivot pour SharePoint &#40;SharePoint 2013&#41;](../instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md).

-   **(2)** le [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] service partagé s’exécute **sur chaque** serveur d’applications et permet à l’application de service de s’exécuter sur **plusieurs** serveurs d’applications. Par conséquent, si un serveur d'applications est mis hors connexion, l'application [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] reste toujours disponible.

-   **(3)** les services de calcul Excel s’exécutent sur un serveur d’applications et permettent à l’application de service de s’exécuter sur plusieurs serveurs d’applications. Par conséquent, si un serveur d'applications est mis hors connexion, Excel Calculation Services reste toujours disponible.

-   **(4)** et **(6)** les instances [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de en mode SharePoint s’exécutent sur des serveurs en dehors de la batterie de serveurs SharePoint, y compris le service Windows **SQL Server Analysis Services (PowerPivot)**. Chacune de ces instances est inscrite auprès d’Excel Services **(3)**. Excel Services gère l'équilibrage de charge des demandes effectuées aux serveurs [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] . L'architecture de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 vous permet d'avoir plusieurs serveurs pour [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] . Vous pouvez ainsi ajouter facilement des instances, si nécessaire. Pour plus d’informations, consultez [Gérer les paramètres de modèle de données Excel Services (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780\(v=office.15\).aspx).

-   **(5)** SQL Server bases de données utilisées pour le contenu, la configuration et les bases de données d’application. Cela inclut la base de données d'application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Le plan de récupération d'urgence doit inclure la couche de base de données. Dans cette conception, les bases de données s’exécutent sur le même serveur que **(4)** l’une des instances [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] . **(4)** et **(5)** peuvent également se trouver sur des serveurs différents.

-   **(7)** forme de sauvegarde ou de redondance de base de données SQL Server.

##  <a name="bkmk_sharepoint2010"></a>Exemple de topologie SharePoint 2010 pour la haute disponibilité PowerPivot
 L'architecture de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 requiert que tous les composants de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] s'exécutent sur les mêmes serveurs d'applications SharePoint. Cela inclut l'instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] déployée en mode SharePoint et deux services partagés, par rapport à un seul dans un déploiement SharePoint 2013.

 Le schéma suivant illustre un exemple de déploiement [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010. Cet exemple prend en charge une bonne disponibilité des services [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] et suppose une sauvegarde régulière des bases de données.

 ![disponibilité powerpivot dans sharepoint 2010](../media/ssas-powerpivot-services-2010.png "disponibilité powerpivot dans sharepoint 2010")

-   **(1)** les serveurs Web frontaux. Installez les fournisseurs de données sur chaque serveur. Pour plus d’informations, voir [Installer le fournisseur OLE DB Analysis Services sur les serveurs SharePoint](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).

-   **(2)** les deux [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] services partagés et **(4)** le service Windows **SQL Server Analysis Services (PowerPivot)** sont installés sur les serveurs d’applications SharePoint.

     Le service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] s'exécute **sur chaque** serveur d'applications et permet à l'application de service de s'exécuter **sur** différents serveurs d'applications. Si un serveur d'applications est mis hors connexion, l'application de service [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] reste toujours disponible.

     Pour augmenter la capacité de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans SharePoint 2010, déployez davantage de serveurs d'applications SharePoint qui exécutent le service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .

-   **(3)** les services de calcul Excel s’exécutent sur chaque serveur d’applications et permettent à l’application de service de s’exécuter sur plusieurs serveurs d’applications. Par conséquent, si un serveur d'applications est mis hors connexion, Excel Calculation Services reste toujours disponible.

-   **(5)** SQL Server bases de données utilisées pour le contenu, la configuration et les bases de données d’application. Cela inclut la base de données d'application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Le plan de récupération d'urgence doit inclure la couche de base de données.

-   **(6)** une forme de sauvegarde ou de redondance de base de données SQL Server.

##  <a name="bkmk_sql_server_technologies"></a>Base de données d’application de service PowerPivot et technologies de disponibilité et de récupération de SQL Server
 Incluez la base de données d’application de service [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] dans votre planification pour une disponibilité élevée SharePoint. Le nom par défaut de la base de données est `DefaultPowerPivotServiceApplicationDB-<GUID>`. Voici un résumé des technologies de disponibilité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et des recommandations pour une utilisation avec la base de données [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] . Pour plus d’informations, consultez [Options de haute disponibilité et de récupération d’urgence prises en charge pour les bases de données SharePoint (SharePoint 2013)](https://technet.microsoft.com/library/jj841106.aspx).

||Commentaires|
|-|--------------|
|
  [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] et [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] dans une batterie de serveurs pour la disponibilité.|Prise en charge mais non recommandée. La recommandation consiste à utiliser AlwaysOn en mode de validation synchrone.|
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] en mode de validation synchrone|Pris en charge et recommandé.|
|
  [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] mise en miroir asynchrone ou envoi de journaux à une autre batterie de serveurs pour la récupération d’urgence.| Pris en charge.|
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] avec validation asynchrone pour la récupération d’urgence|Prise en charge|

-   [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]

-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Envoi de journaux

 Pour plus d'informations sur la façon de planifier un scénario de reprise progressive avec [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], consultez [Récupération d'urgence pour PowerPivot](https://social.technet.microsoft.com/wiki/contents/articles/22137.sharepoint-powerpivot-disaster-recovery.aspx).

## <a name="verification"></a>Vérification
 Pour obtenir des instructions et des scripts pour vous [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] aider à vérifier un déploiement avant et après un cycle de récupération d’urgence, consultez [liste de vérification : utiliser PowerShell pour vérifier PowerPivot pour SharePoint](../instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint.md).

##  <a name="bkmk_more_resources"></a>Liens vers des informations supplémentaires

-   [Options de haute disponibilité et de récupération d’urgence prises en charge pour les bases de données SharePoint (SharePoint 2013)](https://technet.microsoft.com/library/jj841106.aspx)

-   [Planifier la récupération d’urgence (SharePoint Server 2010)](https://technet.microsoft.com/library/ff628971\(v=office.14\).aspx)




