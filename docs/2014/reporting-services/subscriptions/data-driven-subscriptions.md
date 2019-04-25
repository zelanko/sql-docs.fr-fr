---
title: Abonnements pilotés par les données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], data-driven
- data-driven subscriptions
ms.assetid: ba009f62-0d4f-45e7-a27c-36fd5f0cd3a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 964549d535fec50c0ec6e8dc17dd0ef2a1dda221
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62510920"
---
# <a name="data-driven-subscriptions"></a>abonnements pilotés par les données
  Un abonnement piloté par les données constitue un moyen d'utiliser des données d'abonnement dynamiques extraites à partir d'une source de données externe au moment de l'exécution. Un abonnement piloté par les données peut également utiliser du texte statique et des valeurs par défaut que vous spécifiez au moment de définir l'abonnement. Vous pouvez vous servir d'abonnements pilotés par les données pour effectuer les opérations suivantes :  
  
-   Distribuer un rapport à une liste changeante d'abonnés. En l'occurrence, vous utiliserez les abonnements pilotés par les données pour distribuer un rapport dans une vaste organisation où les abonnés varient d'un mois à l'autre ou dans des groupes d'utilisateurs définis à partir d'autres critères.  
  
-   Filtrer la sortie des rapports à l'aide de valeurs de paramètres de rapport extraites au moment de l'exécution.  
  
-   Varier les formats de sortie des rapports et les options de remise pour chaque remise de rapport.  
  
 Un abonnement piloté par les données comprend plusieurs parties. Les éléments fixes d'un abonnement piloté par les données sont définis lorsque vous créez l'abonnement. Il s'agit notamment des éléments suivants :  
  
-   Rapport pour lequel l'abonnement est défini (un abonnement est toujours associé à un rapport unique).  
  
-   Extension de remise employée pour la distribution du rapport. Vous pouvez spécifier une remise par courrier électronique sur le serveur de rapports, une remise sur un partage de fichiers, le fournisseur de remise NULL utilisé pour le préchargement dans le cache ou une extension de remise personnalisée. Vous ne pouvez pas spécifier plusieurs extensions de remise pour un seul et unique abonnement.  
  
-   Source de données des abonnés. Vous devez spécifier une chaîne de connexion à la source de données contenant les données des abonnés au moment de définir l'abonnement. Vous ne pouvez pas spécifier la source de données des abonnés de manière dynamique au moment de l'exécution.  
  
-   Vous devez préciser la requête utilisée pour sélectionner les données des abonnés lors de la définition de l'abonnement. La requête ne peut être modifiée au moment de l'exécution.  
  
 Les valeurs dynamiques adoptées dans un abonnement piloté par les données sont obtenues au cours du traitement de l'abonnement. Des exemples de données de variables susceptibles d'être utilisées dans un abonnement incluent le nom de l'abonné, l'adresse de messagerie, le format de sortie de rapport préféré ou toute valeur de paramètre de rapport valide. Pour utiliser des valeurs dynamiques dans un abonnement piloté par les données, vous devez établir un mappage entre les champs retournés dans la requête selon des options de remise spécifiques et des paramètres de rapport. Les données de variables sont extraites d'une source de données d'abonné à chaque traitement de l'abonnement.  
  
## <a name="requirements-for-using-data-driven-subscriptions"></a>Configuration requise pour utiliser les abonnements pilotés par les données  
 La fonctionnalité d'abonnement piloté par les données n'est pas disponible dans toutes les éditions. Des restrictions s'appliquent également dans le cadre des types de sources de données que vous pouvez utiliser pour extraire des données d'abonnement au moment de l'exécution. La liste ci-dessous fournit de plus amples informations sur les exigences requises :  
  
-   Pour plus d’informations sur les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui prennent en charge la fonctionnalité d’abonnement piloté par les données, consultez [Fonctionnalités prises en charge par les éditions de SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).  
  
-   Pour les données d'abonnement, choisissez une source de données capable de fournir des informations sur les schémas au serveur de rapports. Les données relationnelles [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , les bases de données Oracle et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , les données de package [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , les sources de données ODBC et les sources de données OLE DB sont des exemples de types de sources de données pris en charge. Pour plus d’informations sur les exigences relatives à la source de données des abonnés, consultez [Utiliser une source de données externe pour les données des abonnés &#40;abonnements pilotés par les données&#41;](use-an-external-data-source-for-subscriber-data-data-driven-subscription.md).  
  
## <a name="working-with-data-driven-subscriptions"></a>Utilisation des abonnements pilotés par les données  
 Les rubriques suivantes fournissent des informations supplémentaires sur les abonnements pilotés par les données.  
  
|Rubriques|Description|  
|------------|-----------------|  
|[Créer, modifier et supprimer des abonnements pilotés par les données](data-driven-subscriptions.md)|Explique comment créer, modifier ou supprimer un abonnement piloté par les données.|  
|[Utiliser une source de données externe pour les données des abonnés &#40;abonnements pilotés par les données&#41;](use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)|Fournit des informations sur les sources de données que vous pouvez utiliser pour un abonnement piloté par les données.|  
|[Créer un abonnement piloté par les données &#40;didacticiel SSRS&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md)|Fournit des instructions pas à pas pour apprendre à créer un abonnement piloté par les données.|  
|[Mise en cache de rapports &#40;SSRS&#41;](../report-server/caching-reports-ssrs.md)|Décrit comment utiliser le fournisseur de remise Null avec un abonnement piloté par les données pour précharger la mémoire cache.|  
  
## <a name="see-also"></a>Voir aussi  
 [Abonnements et remise &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md)   
 [Page Créer un abonnement piloté par les données &#40;Gestionnaire de rapports&#41;](../create-data-driven-subscription-page-report-manager.md)   
 [Précharger le cache &#40;Gestionnaire de rapports&#41;](../report-server/preload-the-cache-report-manager.md)  
  
  
