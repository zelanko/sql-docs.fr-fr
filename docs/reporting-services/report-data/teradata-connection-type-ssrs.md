---
title: Type de connexion Teradata | Microsoft Docs
ms.date: 03/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: b02779c2-a6b9-453c-815f-adad53353952
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7fffacee190197125cf283be6ad9263dfae1f1d1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "77081700"
---
# <a name="teradata-connection-type-ssrs"></a>Type de connexion Teradata (SSRS)
  Pour inclure des données de Teradata dans votre rapport, vous devez avoir un dataset basé sur une source de données de rapport de type Teradata. Ce type de source de données intégré est basé sur le fournisseur managé .NET de l'extension pour le traitement des données Teradata.  
  
 Utilisez les informations de cette rubrique pour générer une source de données. Pour obtenir des instructions détaillées, consultez [Ajouter et vérifier une connexion de données &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a> Chaîne de connexion  
 Contactez l'administrateur de votre base de données pour connaître les informations de connexion et d'identification à utiliser pour se connecter à la source de données. L’exemple de chaîne de connexion suivant spécifie une source de données Teradata sur le serveur indiqué avec l’adresse IP :  
  
```  
data source=<IP Address>  
```  
  
 Pour obtenir d’autres exemples sur les chaînes de connexion, consultez [Créer des chaînes de connexion de données - Générateur de rapports et SSRS](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
##  <a name="Credentials"></a> Informations d'identification  
 Les informations d'identification sont obligatoires pour exécuter des requêtes, afficher l'aperçu du rapport localement et afficher l'aperçu du rapport à partir du serveur de rapports.  
  
 Après avoir publié votre rapport, vous pouvez devoir modifier les informations d'identification pour la source de données afin que les autorisations soient valides pour récupérer les données lorsque le rapport s'exécute sur le serveur de rapports.  
  
 Pour plus d’informations, consultez [Créer des chaînes de connexion de données - Générateur de rapports et SSRS](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md) ou [Spécifier des informations d’identification et de connexion pour les sources de données de rapport](specify-credential-and-connection-information-for-report-data-sources.md).  
  
  
##  <a name="Remarks"></a> Notes  
 Avant de pouvoir connecter une source de données Teradata, l’administrateur système doit installer au préalable la version du fournisseur de données .NET pour Teradata qui prend en charge la récupération des données à partir de Teradata. Ce fournisseur de données doit être installé sur le même ordinateur que le Générateur de rapports, ainsi que sur le serveur de rapports.  
  
 Certains modes de remise de rapport ne sont pas pris en charge par ce fournisseur de données. La remise des rapports par le biais d'abonnements pilotés par les données n'est pas prise en charge pour cette extension pour le traitement des données. Pour plus d’informations, consultez [Utiliser une source de données externe pour les données des abonnés &#40;abonnements pilotés par les données&#41;](../../reporting-services/subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md).  
  
  
##  <a name="Models"></a> Modèles de rapport  
 Pour créer un dataset à partir d'un modèle de rapport basé sur une source de données Teradata, le modèle doit être conçu dans le Générateur de modèles dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] et publié sur un serveur de rapports.  
  
  
##  <a name="Related"></a> Sections connexes  
 Ces sections de la documentation fournissent des informations de fond d'ordre conceptuel sur les données de rapport, ainsi que des informations sur les procédures de définition, de personnalisation et d'utilisation des parties d'un rapport qui sont liées aux données.  
  
 [Datasets de rapport &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)  
 Fournit une vue d'ensemble de l'accès aux données pour votre rapport.  
  
 [Créer des chaînes de connexion de données - Générateur de rapports et SSRS](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
 Fournit des informations sur les connexions de données et les sources de données.  
  
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Fournit des informations sur les datasets incorporés et partagés.  
  
 [Collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
 Fournit des informations sur la collection de champs générée par la requête de dataset.  
  
 La rubrique [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md) offre des informations détaillées sur la prise en charge des plateformes et des versions pour chaque extension de données.  
 
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  
