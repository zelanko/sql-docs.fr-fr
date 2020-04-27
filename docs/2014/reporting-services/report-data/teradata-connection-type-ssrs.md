---
title: Type de connexion Teradata (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b02779c2-a6b9-453c-815f-adad53353952
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4a47fb239121b1e354923fc42ed3da29716fdba5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66107017"
---
# <a name="teradata-connection-type-ssrs"></a>Type de connexion Teradata (SSRS)
  Pour inclure les données d'une base de données relationnelle Teradata dans votre rapport, vous devez avoir un dataset basé sur une source de données de rapport de type Teradata. Ce type de source de données intégré est basé sur le fournisseur managé .NET de l'extension pour le traitement des données Teradata.  
  
 Utilisez les informations de cette rubrique pour générer une source de données. Pour obtenir des instructions pas à pas, consultez [Ajouter et vérifier une connexion de données ou une source de données &#40;générateur de rapports et des&#41;SSRS ](add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="connection-string"></a><a name="Connection"></a> Chaîne de connexion  
 Contactez l'administrateur de votre base de données pour connaître les informations de connexion et d'identification à utiliser pour se connecter à la source de données. L'exemple de chaîne de connexion suivant spécifie une base de données Teradata sur le serveur indiqué avec l'adresse IP :  
  
```  
data source=<IP Address>  
```  
  
 Pour obtenir d’autres exemples sur les chaînes de connexion, consultez [Connexions de données, sources de données et chaînes de connexion dans le Générateur de rapports](../data-connections-data-sources-and-connection-strings-in-report-builder.md).  
  
##  <a name="credentials"></a><a name="Credentials"></a> Informations d'identification  
 Les informations d'identification sont obligatoires pour exécuter des requêtes, afficher l'aperçu du rapport localement et afficher l'aperçu du rapport à partir du serveur de rapports.  
  
 Après avoir publié votre rapport, vous pouvez devoir modifier les informations d'identification pour la source de données afin que les autorisations soient valides pour récupérer les données lorsque le rapport s'exécute sur le serveur de rapports.  
  
 Pour plus d’informations, consultez [connexions de données, sources de données et chaînes de connexion dans Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) ou [spécifier des informations d’identification dans générateur de rapports](../specify-credentials-in-report-builder.md).  

##  <a name="remarks"></a><a name="Remarks"></a> Notes  
 Avant de pouvoir connecter une source de données Teradata, l'administrateur système doit installer au préalable la version du fournisseur de données .NET pour Teradata qui prend en charge la récupération des données à partir de la base de données Teradata. Ce fournisseur de données doit être installé sur le même ordinateur que le Générateur de rapports, ainsi que sur le serveur de rapports.  
  
 Certains modes de remise de rapport ne sont pas pris en charge par ce fournisseur de données. La remise des rapports par le biais d'abonnements pilotés par les données n'est pas prise en charge pour cette extension pour le traitement des données. Pour plus d’informations, consultez [Utiliser une source de données externe pour les données des abonnés &#40;abonnement piloté par les données&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md) dans la documentation de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] dans la documentation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [en ligne](https://go.microsoft.com/fwlink/?linkid=121312)de.  

##  <a name="report-models"></a><a name="Models"></a> Modèles de rapport  
 Pour créer un dataset à partir d'un modèle de rapport basé sur une source de données Teradata, le modèle doit être conçu dans le Générateur de modèles dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] et publié sur un serveur de rapports.  

##  <a name="related-sections"></a><a name="Related"></a> Sections connexes  
 Ces sections de la documentation fournissent des informations de fond d'ordre conceptuel sur les données de rapport, ainsi que des informations sur les procédures de définition, de personnalisation et d'utilisation des parties d'un rapport qui sont liées aux données.  
  
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-datasets-ssrs.md)  
 Fournit une vue d'ensemble de l'accès aux données pour votre rapport.  
  
 [Connexions de données, sources de données et chaînes de connexion dans le Générateur de rapports](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 Fournit des informations sur les connexions de données et les sources de données.  
  
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Fournit des informations sur les datasets incorporés et partagés.  
  
 [Collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)  
 Fournit des informations sur la collection de champs générée par la requête de dataset.  
  
 [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) dans la section [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [documentation en ligne](https://go.microsoft.com/fwlink/?linkid=121312) de .  
 Fournit des informations détaillées sur la prise en charge des plateformes et des versions pour chaque extension de données.  
  
 [Using SQL Server 2008 Reporting Services with the .NET Framework Data Provider for Teradata (éventuellement en anglais)](https://go.microsoft.com/fwlink/?LinkID=130848)  
 Fournit des informations détaillées sur l'utilisation de cette extension de données.  

## <a name="see-also"></a>Voir aussi  
 [Paramètres de rapport &#40;Générateur de rapports et de Concepteur de rapports&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtrer, regrouper et trier les données &#40;Générateur de rapports et SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
