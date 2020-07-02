---
title: 'Nettoyer les données à l’aide de données de référence de connaissances (externes) '
description: Découvrez comment nettoyer les données à l’aide des connaissances des fournisseurs de données de référence avec Data Quality Services (DQS) dans SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 158009e9-8069-4741-8085-c14a5518d3fc
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 199eac229d752cb019ec027124e83c85ead0176c
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85813892"
---
# <a name="cleanse-data-using-external-knowledge-reference-data---data-quality-services-dqs"></a>Nettoyer les données à l’aide de données de référence de connaissances (externes)-Data Quality Services (DQS)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Cette rubrique décrit comment nettoyer les données à l'aide de la connaissance des fournisseurs de données de référence. Toutes les étapes d’exécution du nettoyage restent les mêmes pour nettoyer vos données à l’aide de la connaissance des fournisseurs de données de référence, comme expliqué dans [Nettoyer des données à l’aide de la base de connaissance DQS &#40;interne&#41;](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md). Cette rubrique fournit des informations spécifiques sur le nettoyage des données à l’aide du service des données de référence dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).  

> [!IMPORTANT]
> Cet article mentionne des services de données de référence tiers qui étaient disponibles dans Azure DataMarket. DataMarket et Data Services, notamment les données d’adresse Melissa par exemple, ont été supprimés après le 31/12/2016. Par conséquent, vous ne pouvez plus exécuter les exemples de cet article avec les services spécifiés de DataMarket. Vous pouvez quand même utiliser les services de données de référence directement disponibles en ligne des fournisseurs de données de référence tiers.
 
 Lorsque vous utilisez la fonction du service des données de référence dans DQS pour nettoyer vos données, le processus de nettoyage DQS envoie les valeurs du domaine mappé au fournisseur de services de données de référence sous forme de demande de traitement. Le service de données de référence répond avec les informations suivantes :  
  
-   Correction suggérée  
  
-   Confiance  
  
-   Informations supplémentaires sur le domaine mappé. Les données de référence peuvent également normaliser, analyser ou enrichir la source avec des informations supplémentaires. Ces informations sont fournies dans des champs supplémentaires de la réponse.  
  
 Après l'obtention de la réponse du service de données de référence, les événements suivants se produisent dans DQS pendant l'activité de nettoyage :  
  
-   Selon les valeurs **Seuil de correction automatique** et **Confiance minimale** spécifiées pendant le mappage des domaines avec le service de données de référence, les valeurs du domaine sont automatiquement corrigées or suggérées en fonction du niveau de confiance.  
  
    > [!NOTE]  
    >  Les valeurs de seuil que vous spécifiez pendant le mappage d'un domaine à un service de données de référence sont appliquées tout en nettoyant les données à l'aide de la connaissance du service des données de référence, et non celles spécifiées dans l'onglet **Paramètres généraux** de la section **Configuration** . Pour plus d’informations sur la spécification des valeurs de seuil pour le nettoyage des données de référence, consultez l’étape 9 dans [Attacher un domaine ou un domaine composite à des données de référence](../data-quality-services/attach-domain-or-composite-domain-to-reference-data.md).  
  
-   Les valeurs de domaine sont classées par catégorie comme suit : **Suggérées**, **Nouvelles**, **Non valides**, **Corrigées**et **Correctes**.  
  
-   Les informations supplémentaires sont ajoutées à la source, puis les informations sont disponibles avec les données nettoyées pour l'exportation.  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Conditions préalables  
 Vous devez avoir mappé les domaines obligatoires d'une base de connaissances DQS au service de données de référence approprié. En outre, la base de connaissances doit contenir la connaissance sur le type de données que vous souhaitez nettoyer. Par exemple, si vous souhaitez nettoyer les données sources qui contiennent des adresses américaines, vous devez mapper les domaines à un fournisseur de services de données de référence qui propose des données de haute qualité pour les adresses américaines. Pour plus d’informations, consultez [Attacher un domaine ou un domaine composite à des données de référence](../data-quality-services/attach-domain-or-composite-domain-to-reference-data.md).  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Vous devez disposer du rôle dqs_kb_editor ou dqs_kb_operator sur la base de données DQS_MAIN pour effectuer le nettoyage des données.  
  
##  <a name="cleanse-your-data-using-reference-data-knowledge"></a><a name="Cleanse"></a> Nettoyer les données à l'aide de la connaissance des données de référence  
 Nous poursuivrons avec le même exemple d’utilisation des domaines que nous avons mappés dans la rubrique précédente, attacher un domaine [ou un domaine composite à des données de référence](../data-quality-services/attach-domain-or-composite-domain-to-reference-data.md), avec le service de données Melissa dans la place de marché Azure. Maintenant, nous utiliserons les mêmes domaines pour nettoyer certains exemples d'adresses américaines. Les étapes du nettoyage des données sont les mêmes que celles décrites dans [Nettoyer des données à l’aide de la base de connaissances DQS &#40;interne&#41;](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md). Toutefois, nous attirerons votre attention chaque fois que nécessaire pendant le processus.  
  
1.  Créez un projet de qualité des données, puis sélectionnez l'activité **Nettoyage** . Consultez [Create a Data Quality Project](../data-quality-services/create-a-data-quality-project.md).  
  
2.  Dans la page **Mapper** , mappez les 4 domaines suivants avec les colonnes appropriées de votre source de données : **Adresse**, **Ville**, **État**et **Code postal**. Cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  Lorsque vous avez mappé les 4 domaines du domaine composite de **Contrôle d'adresse** , le nettoyage des données sera effectué au niveau du domaine composite, et non au niveau du domaine individuel.  
  
3.  Sur la page **Nettoyer** , exécutez le processus de nettoyage assisté par ordinateur en cliquant sur **Démarrer**. Une fois le processus de nettoyage terminé, cliquez **Suivant**.  
  
    > [!NOTE]  
    >  Sur la page **Nettoyer** , DQS affiche les informations sur les domaines joints au service des données de référence de deux façons :  
    >   
    >  -   Un message s’affiche sous le bouton **Démarrer** : «domaines \<Domain1> , \<Domain2> ,... \<DomainN> sont nettoyés à l’aide du fournisseur de services de données de référence.» Dans cet exemple, le message suivant s’affiche : « La vérification d’adresse de domaine est nettoyée à l’aide du fournisseur de services de données de référence. »  
    > -   Une icône, ![domaine est attachée à RDS](../data-quality-services/media/dqs-rdsindicator.JPG "Domaine attaché au RDS"), s’affiche dans la zone du **profileur** par rapport aux domaines attachés au fournisseur de services de données de référence. Dans cet exemple, l'icône sera affichée sur le domaine composite **Contrôle d'adresse** .  
  
4.  Dans la page **Gérer et afficher les résultats** , vérifiez les valeurs de domaine. Le service de données de référence peut afficher plusieurs suggestions, si elles sont disponibles, pour une valeur en fonction du nombre maximal de suggestions spécifiées dans la zone **Candidats suggérés** lors du mappage du domaine au service des données de référence. Par exemple, deux suggestions s'affichent pour l'adresse américaine suivante :  
  
     **Valeur d’origine :**  
  
    |Adresse|City|State (État)|Zip|  
    |------------------|----------|-----------|---------|  
    |1 MSFT way|Redmond||98052|  
  
     **Valeurs suggérées :**  
  
    |Adresse|City|State (État)|Zip|  
    |------------------|----------|-----------|---------|  
    |1 Microsoft Way|Redmond|WA|98052|  
    |PO Box 1|Redmond|WA|98073|  
  
     ![Nettoyage à l'aide du service de données de référence](../data-quality-services/media/dqs-rdscleansing.JPG "Nettoyage à l'aide du service de données de référence")  
  
    > [!NOTE]  
    >  Pour les domaines composites, DQS met aussi en surbrillance les domaines d'une couleur différente qui ont été corrigés pendant le processus de nettoyage assisté par ordinateur. Par exemple, dans ce cas, **Adresse** et **État** ont été corrigés et mis en surbrillance avec la couleur cyan.  
  
5.  Une fois que vous avez fini d'examiner toutes les valeurs de domaine, cliquez sur **Suivant** pour exporter les données.  
  
6.  Dans la page **Exporter** , vous remarquerez qu'en dehors des informations standard sur l'activité de nettoyage pour chaque domaine (source, raison, confiance et état), il existe des informations supplémentaires fournies par le service des données de référence Melissa, telles que la latitude et la longitude de votre adresse, le nom du département, le type d'adresse (avenue, rue, etc.), et ainsi de suite.  
  
7.  Exportez vos données vers la destination requise (SQL Server, CSV ou Excel), puis cliquez sur **Terminer** pour fermer le projet.  
  
    > [!IMPORTANT]  
    >  Si vous utilisez une version 64 bits d'Excel, vous ne pouvez pas exporter les données nettoyées vers un fichier Excel : vous ne pouvez exporter que vers une base de données SQL Server ou un fichier .csv.  
  
  
