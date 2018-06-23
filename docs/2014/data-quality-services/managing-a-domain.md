---
title: Gestion d’un domaine | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5ab71a3-0dac-45b1-be8e-93bf7e0e03ce
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 72b2400e8a953490d1650a8e435c6b353c660445
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040723"
---
# <a name="managing-a-domain"></a>Gestion d'un domaine
  Cette rubrique décrit l'utilisation des domaines dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Un domaine contient une représentation sémantique des données dans un champ spécifique dans la source de données qui doit être analysée. Un domaine fait partie de la base de connaissances que vous créez pour une source de données, et la connaissance que vous accumulez en analysant un exemple de source de données, ou lors de l'importation de données, est ajoutée aux domaines définis dans la base de connaissances. La connaissance de ces domaines est utilisée ultérieurement pour effectuer le nettoyage et la correspondance dans un projet de qualité des données. Les domaines sont au cœur de toutes les activités dans Data Quality Services.  
  
 Un domaine est mappé à un champ de source de données et est rempli lors des activités de découverte des connaissances, de gestion de l'arborescence du domaine et de correspondance. Le mode de chargement des données de la source de données et de génération des données dans un rapport est défini dans les propriétés de domaine. Lorsque vous utilisez un fournisseur de données de référence pour nettoyer les données, vous attachez un service de données de référence à un domaine unique ou composite. Vous créez des règles à appliquer à vos données dans un domaine, et vous pouvez créer des relations à base de termes pour un domaine. Vous pouvez afficher et corriger les données du domaine.  
  
 Vous pouvez également créer un domaine composite qui est constitué de plusieurs domaines individuels qui contiennent chacun des connaissances sur des données communes. Pour plus d’informations, consultez [Gestion d’un domaine composite](../../2014/data-quality-services/managing-a-composite-domain.md).  
  
## <a name="domain-properties"></a>Propriétés du domaine  
 Lorsque vous créez un domaine, vous disposez des options suivantes pour remplir le domaine à partir des données sources et générer les valeurs de domaine. Pour plus d’informations, voir [Définir les propriétés du domaine](../../2014/data-quality-services/set-domain-properties.md).  
  
-   Sélectionnez le type des données avec lesquelles vous remplissez le domaine. Pour plus d'informations sur les types de données pris en charge pour chaque type de données de domaine, consultez [Types de données SQL Server et SSIS pris en charge pour les domaines DQS](../../2014/data-quality-services/supported-sql-server-and-ssis-data-types-for-dqs-domains.md).  
  
-   Spécifiez que seules les valeurs de début, et non leurs synonymes, seront sorties du domaine.  
  
-   Spécifiez que les valeurs de domaine seront sorties sous un certain format, selon le type de données.  
  
-   Si le type de données est une chaîne, vous pouvez normaliser la chaîne en supprimant les caractères spéciaux lorsque la chaîne est chargée à partir de la source de données dans le domaine.  
  
-   Si le type de données est une chaîne, vous pouvez exécuter le vérificateur d'orthographe DQS pour vérifier la syntaxe, l'orthographe et la structure de phrase de la chaîne, et indiquer toutes les erreurs potentielles dans la page **Valeurs du domaine** de **Gestion de l'arborescence du domaine**. Cela inclut l'indication de la langue dans laquelle le vérificateur d'orthographe s'exécutera.  
  
-   Si le type de données est une chaîne, vous pouvez spécifier que DQS ne doit pas reconnaître les erreurs de syntaxe lorsque vous savez que des erreurs de syntaxe ne se produiront pas dans les chaînes.  
  
## <a name="in-this-section"></a>Dans cette section  
 L'utilisation d'un domaine vous permet d'effectuer les opérations suivantes :  
  
|||  
|-|-|  
|Créer une représentation sémantique d'un champ de données avec un type de données spécifique, spécifier comment le domaine est rempli et mettre en forme la sortie du domaine|[Créer un domaine](../../2014/data-quality-services/create-a-domain.md)|  
|Lier un domaine à un autre domaine, en lui permettant de partager les mêmes paramètres et valeurs|[Créer un domaine lié](../../2014/data-quality-services/create-a-linked-domain.md)|  
|Attacher un service de données de référence à un domaine unique ou composite|[Joindre un domaine ou un domaine Composite aux données de référence](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)|  
|Modifier ou augmenter les valeurs dans une base de connaissances|[Modifier les valeurs de domaine](../../2014/data-quality-services/change-domain-values.md)|  
|Utiliser les règles de validation et de normalisation|[Créer une règle de domaine](../../2014/data-quality-services/create-a-domain-rule.md)|  
|Utiliser des relations pour corriger un terme qui fait partie d'une valeur dans un domaine|[Créer des relations à base de termes](../../2014/data-quality-services/create-term-based-relations.md)|  
|Effectuer, fermer ou annuler l'activité de gestion de l'arborescence du domaine|[Terminer l’activité de gestion de l’arborescence du domaine](../../2014/data-quality-services/end-the-domain-management-activity.md)|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Construction d'une base de connaissances par la découverte de la connaissance et la gestion interactive de la connaissance|[Construction d’une base de connaissances](../../2014/data-quality-services/building-a-knowledge-base.md)|  
|Importation ou exportation de la connaissance depuis ou vers une base de connaissances.|[Importation et exportation de connaissances](../../2014/data-quality-services/importing-and-exporting-knowledge.md)|  
|Création d'un domaine composite et ajout de connaissances au domaine.|[Gestion d’un domaine composite](../../2014/data-quality-services/managing-a-composite-domain.md)|  
  
  