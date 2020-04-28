---
title: Services de données de référence dans DQS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ef217717-6d05-443e-af26-44dc745a349d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: f4f7c1003db22721d9140c166b1ed03e72b9ab0f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "70154428"
---
# <a name="reference-data-services-in-dqs"></a>Services de données de référence dans DQS
  Les données de référence correspondent à un ensemble précis et complet de données globales associées ou classées (au-delà des limites d'une entreprise) qui sont disponibles pour les domaines publics approuvés ou auprès de fournisseurs de contenu commercial de premier ordre.  
  
 Dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS), la fonctionnalité de service de données de référence vous permet de vous abonner à des fournisseurs de données de référence tiers, ainsi que de nettoyer et d'enrichir facilement vos données métier en les validant par rapport à leurs données de grande qualité. Vous pouvez utiliser les services des meilleurs fournisseurs de services de qualité des données à partir de DQS pour normaliser, corriger ou enrichir vos données pendant le processus de nettoyage. Par exemple, vous pouvez confronter une liste d'indicatifs régionaux ou de codes postaux aux données de référence pour valider les adresses de vos clients.  
  
 La fonctionnalité de service de données de référence présente les avantages suivants :  
  
-   Les données de référence vous permettent de garantir la qualité de vos données en les comparant à des données garanties par une société tierce.  
  
-   Le processus de données de référence est incorporé dans la création d'une base de connaissances DQS et un projet de qualité des données, ce qui vous permet d'instituer un processus de qualité des données complet.  
  
-   Prend en charge l’utilisation de données de référence provenant de la place de marché Azure et directement de fournisseurs de données de référence tiers.  
  
##  <a name="using-reference-data-from-azure-marketplace"></a><a name="Marketplace"></a>Utilisation de données de référence à partir de la place de marché Azure  
 DQS prend en charge l’utilisation de données de référence de la place de marché Azure pour permettre aux fournisseurs de contenu de fournir des services de données de référence via Marketplace. Marketplace est un service Microsoft qui fournit un canal de remise et de marché unique permettant d'obtenir des données et des applications de haute qualité sous la forme de services en nuage. Pour plus d’informations sur Marketplace, consultez [en savoir plus sur](https://azuremarketplace.microsoft.com/marketplace/)la place de marché Azure.  
  
 L'intégration transparente entre la Place de marché et DQS simplifie les étapes associées à la découverte, l'exploration et l'acquisition d'informations pour des projets de qualité des données à partir de DQS. Les données sont utilisées à partir de DQS, et permettent aux utilisateurs de DQS d'atteindre une haute qualité de données en rassemblant de façon innovante DQS, Marketplace et des fournisseurs de services de données de référence.  
  
 Pour utiliser des données de référence de marché dans DQS pour l'activité de nettoyage, vous devez disposer d'une clé de compte Marketplace. La création d'une clé de compte Marketplace est gratuite ; vous payez uniquement si vous vous abonnez à des datasets payés. L'abonnement à des datasets gratuits et leur utilisation n'entraînent aucun frais. Pour plus d’informations sur la création d’une clé de compte Marketplace, consultezhttps://go.microsoft.com/fwlink/?LinkId=212936) [créer votre compte](https://go.microsoft.com/fwlink/?LinkId=212936) (.  
  
 En outre, vous pouvez effectuer les activités Marketplace suivantes à partir de DQS :  
  
-   parcourir des jeux de données dans Marketplace ;  
  
-   créer une clé de compte Marketplace ;  
  
-   gérer les détails de votre compte Marketplace, tels que les clés de compte et les abonnements à des fournisseurs de données.  
  
 Vous pouvez effectuer ces activités sous l'onglet **Données de référence** de l'écran **Configuration** dans [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
##  <a name="using-reference-data-directly-from-the-third-party-reference-data-providers"></a><a name="Direct"></a> Utilisation de données de référence provenant directement de fournisseurs de données de référence tiers  
 Si vous n’êtes pas connecté à Internet et que vous ne pouvez donc pas utiliser Marketplace, DQS prend également en charge la connexion directe à des fournisseurs de données disponibles dans le réseau de votre organisation. Pour utiliser des données de référence provenant de fournisseurs de données de référence tiers en ligne directs, vous devez créer un enregistrement pour le fournisseur de données dans DQS.  
  
##  <a name="how-to-cleanse-data-by-using-the-reference-data"></a><a name="HowToCleanse"></a> Procédure : nettoyer des données à l'aide de données de référence  
 Le nettoyage de vos données dans DQS à l'aide de données de référence inclut les trois étapes suivantes :  
  
1.  **Configuration des détails du fournisseur de données de référence dans DQS**: avant de pouvoir utiliser des données de référence dans DQS, vous devez configurer les détails du service de données de référence dans DQS.  
  
    1.  Si vous utilisez Marketplace, fournissez une clé de compte Marketplace valide, accédez à la catégorie de données [Data Quality Services](../data-quality-services/data-quality-services.md) dans Marketplace, et abonnez-vous aux fournisseurs requis.  
  
    2.  Si vous utilisez un fournisseur de données de référence en ligne direct, vous devez ajouter les détails du fournisseur de données de référence direct dans DQS avant de pouvoir l'utiliser.  
  
     La configuration des détails de fournisseur de données de référence dans DQS est une activité qui s'effectue une seule fois pour un fournisseur de données particulier. Seuls les administrateurs DQS peuvent configurer des paramètres de données de référence dans DQS.  
  
2.  **Mappage d'un domaine/domaine composite dans une base de connaissances au service de données de référence**: mappez un domaine/domaine composite au service de données de référence approprié souscrit/ajouté à l'étape 1.  
  
3.  **Utilisation des domaines mappés pour l'activité de nettoyage dans un projet de qualité des données**: lors de la création d'un projet de qualité des données pour l'activité **Nettoyage** , sélectionnez la base de connaissances qui contient des domaines/domaines composites mappés avec des services de données de référence à l'étape 2, puis effectuez l'activité de nettoyage.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Explique comment configurer DQS pour utiliser des services de données de référence provenant de Marketplace ou de fournisseurs de données tiers en ligne directs.|[Configurer DQS pour utiliser des données de référence](../../2014/data-quality-services/configure-dqs-to-use-reference-data.md)|  
|Explique comment mapper un domaine/domaine composite dans une base de connaissances à un service de données de référence.|[Attacher un domaine ou un domaine composite à des données de référence](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)|  
|Explique comment nettoyer des données à l'aide d'un service de données de référence.|[Nettoyer des données à l’aide de la connaissance des données de référence &#40;externes&#41;](../../2014/data-quality-services/cleanse-data-using-reference-data-external-knowledge.md)|  
  
  
