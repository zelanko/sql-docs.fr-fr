---
title: Administration et configuration du serveur PowerPivot dans l’administration centrale | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2cdbfdc5-45a9-4000-a03d-318cc7ac8fe9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: de72001ced1b7e2690f90b2de4c59bb35aca6ce4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66071112"
---
# <a name="powerpivot-server-administration-and-configuration-in-central-administration"></a>Administration et configuration d'un serveur PowerPivot dans l'Administration centrale
  L'administration et la configuration du serveur PowerPivot sont gérées par les administrateurs d'application de service SharePoint à l'aide de l'Administration centrale SharePoint.  
  
 PowerPivot pour SharePoint doit être configuré avant de pouvoir être utilisé. Après avoir installé PowerPivot pour SharePoint à l'aide du programme d'installation de SQL Server, vous pouvez le configurer à l'aide d'une des approches suivantes :  
  
-   Outil de configuration de PowerPivot ou outil de configuration de PowerPivot pour SharePoint 2013  
  
-   Démarrez l'Administration centrale de SharePoint.  
  
-   Applets de commande PowerShell  
  
 Ces trois méthodes permettent d'obtenir un serveur entièrement configuré.  
  
 Cette section présente les tâches requises pour configurer le logiciel à l'aide de l'Administration centrale. Au minimum, vous devez effectuer les trois tâches de configuration obligatoires répertoriées dans la liste ci-dessous.  
  
> [!IMPORTANT]  
>  Pour SharePoint 2010, SharePoint 2010 Service Pack 1 (SP1) doit être installé avant de pouvoir configurer PowerPivot pour SharePoint, ou une batterie de serveurs SharePoint qui utilise un serveur de base de données [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Si vous n'avez pas encore installé le Service Pack, faites-le maintenant avant de commencer la configuration du serveur.  
  
## <a name="benefits-of-configuring-powerpivot-for-sharepoint-using-central-administration"></a>Avantages de la configuration de PowerPivot pour SharePoint à l'aide de l'Administration centrale  
 L'Administration centrale de SharePoint est l'application d'administration d'une batterie de serveurs SharePoint. Si vous êtes administrateur de batterie, vous préférerez peut-être utiliser un outil familier pour ajouter une instance de PowerPivot pour SharePoint à votre batterie.  
  
 Contrairement aux outils de configuration de PowerPivot ou aux applets de commande PowerShell, l'Administration centrale fournit des pages qui spécifient toutes les options que vous pouvez définir lors de la configuration d'une application ou d'un serveur. Les autres méthodes réduisent le nombre d'étapes impliquées dans le flux de travail de configuration, ou nécessitent des connaissances préalables concernant la configuration d'un serveur SharePoint à l'aide de PowerShell.  
  
## <a name="related-content"></a>Contenu associé  
 [Configuration de PowerPivot à l’aide de Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)  
  
 [Outils de configuration de PowerPivot](power-pivot-configuration-tools.md)  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Lien|Type|Description de la tâche|  
|----------|----------|----------------------|  
|[Déployer des solutions PowerPivot sur SharePoint](deploy-power-pivot-solutions-to-sharepoint.md)|Obligatoire|Cette étape installe les fichiers solutions qui ajoutent les fichiers programme et les pages d'application à la batterie de serveurs et aux collections de sites.|  
|[Créer et configurer une application de service PowerPivot dans l'Administration centrale](create-and-configure-power-pivot-service-application-in-ca.md)|Obligatoire|Cette étape configure le service système PowerPivot.|  
|[Activer la fonctionnalité d'intégration PowerPivot pour des collections de sites dans l'Administration centrale](activate-power-pivot-integration-for-site-collections-in-ca.md)|Obligatoire|Cette étape active les fonctionnalités PowerPivot au niveau de la collection de sites.|  
|[Ajouter MSOLAP.5 comme fournisseur de données approuvé dans Excel Services](add-msolap-5-as-a-trusted-data-provider-in-excel-services.md)|Obligatoire|Cette étape ajoute le fournisseur OLE DB Analysis Services en tant que fournisseur approuvé dans Excel Services.|  
|[Actualisation des données PowerPivot avec SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md)|Recommandé|L'actualisation des données est facultative mais recommandée. Elle vous permet de planifier les mises à jour sans assistance des données PowerPivot dans les classeurs Excel publiés.|  
|[Configurez le compte d’actualisation des données PowerPivot sans assistance &#40;PowerPivot pour SharePoint&#41;](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md)|Recommandé|Cette étape configure un compte spécial qui peut être utilisé pour exécuter des travaux d'actualisation des données sur le serveur.|  
|[Configurer la collecte des données d’utilisation pour &#40;PowerPivot pour SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)|Facultatif|La collecte des données d'utilisation est configurée par défaut. Vous pouvez utiliser ces étapes pour modifier les paramètres par défaut.|  
|[Configurez l’actualisation des données dédiées ou le traitement des requêtes uniquement &#40;PowerPivot pour SharePoint&#41;](../configure-dedicated-data-refresh-query-only-processing-powerpivot-sharepoint.md)|Facultatif|Une instance PowerPivot peut être consacrée uniquement aux travaux ou requêtes d'actualisation des données. En outre, vous pouvez modifier les paramètres par défaut pour les travaux parallèles d'actualisation des données.|  
|[Configurer des comptes de service PowerPivot](configure-power-pivot-service-accounts.md)|Facultatif|Explique comment mettre à jour les mots de passe ou modifier les comptes de service.|  
|[Connecter une application de service PowerPivot à une application Web SharePoint dans l'Administration centrale](connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md)|Facultatif|Explique comment modifier les associations de service.|  
|[Créer un emplacement approuvé pour les sites PowerPivot dans l'Administration centrale](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)|Facultatif|Explique comment ajouter la galerie PowerPivot en tant qu'emplacement approuvé.|  
|[Configurer et afficher les fichiers journaux SharePoint et la journalisation des diagnostics &#40;PowerPivot pour SharePoint&#41;](configure-and-view-sharepoint-and-diagnostic-logging.md)|Facultatif|La journalisation des événements est configurée par défaut. Vous pouvez utiliser ces étapes pour modifier les paramètres par défaut.|  
|[Règles d'intégrité de PowerPivot - Configurer](configure-power-pivot-health-rules.md)|Facultatif|Les règles d'intégrité du serveur sont configurées par défaut. Vous pouvez utiliser ces étapes pour modifier certains paramètres par défaut.|  
|[Créer et personnaliser une Galerie PowerPivot](create-and-customize-power-pivot-gallery.md)|Facultatif|Pour les installations que vous configurez manuellement, cette procédure explique comment créer une bibliothèque Galerie PowerPivot qui affiche des images miniatures des classeurs PowerPivot qu'elle contient.|  
|[Ajoutez un type de contenu de connexion de modèle sémantique BI à une bibliothèque &#40;PowerPivot pour SharePoint&#41;](add-bi-semantic-model-connection-content-type-to-library.md)|Facultatif|Explique comment étendre une bibliothèque de documents pour prendre en charge la création de fichiers de connexion de modèles sémantiques BI.|  
  
## <a name="see-also"></a>Voir aussi  
 [Installation de PowerPivot pour SharePoint 2010](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)   
 [Référence du paramètre de configuration &#40;PowerPivot pour SharePoint&#41;](configuration-setting-reference-power-pivot-for-sharepoint.md)   
 [Récupération d'urgence pour PowerPivot pour SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=389570)  
  
  
