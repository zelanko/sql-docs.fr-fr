---
title: 'Leçon 4 : Stockage des données des fournisseurs dans MDS | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: bacd9eaf-4d12-4f25-aec7-d785dec1b623
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 678a7d6ce075e6a1082856aa7962bb3f6eec522d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65489717"
---
# <a name="lesson-4-storing-supplier-data-in-mds"></a>Leçon 4 : Stockage des données sur les fournisseurs dans MDS
  Master Data Services (MDS) est une solution SQL Server de gestion des données de référence. La gestion des données de référence (MDM) correspond aux efforts d'une organisation en vue de découvrir et de définir des listes de données non transactionnelles.  
  
 Les modèles correspondent au niveau le plus élevé de l'organisation dans Master Data Services, et organisent la structure de vos données de référence. Votre implémentation MDS peut comporter un ou plusieurs modèles où chaque modèle regroupe des données similaires. En général, les données de référence peuvent figurer dans l'une des quatre catégories suivantes : personnes, lieux, choses ou concepts. Par exemple, vous pouvez créer un modèle Product pour contenir des données relatives à un produit ou un modèle Customer pour contenir des données relatives à un client. Consultez [Modèles (Master Data Services)](https://msdn.microsoft.com/library/ee633746.aspx) pour plus de détails.  
  
 Un modèle peut contenir une ou plusieurs entités. Chaque entité a des attributs (colonnes) et des membres (lignes). Chaque ligne contient les données de référence. Dans cette leçon, vous allez créer un modèle Fournisseurs avec deux entités nommées Fournisseur et État. L’entité fournisseur a les attributs suivants : Code, nom, prénom du Contact, nom du Contact, contactez l’adresse de messagerie, ligne d’adresse, ville, état, Zip et pays. Consultez [Attributs (Master Data Services)](https://msdn.microsoft.com/library/ee633745.aspx) pour plus d'informations sur les attributs en général. Les attributs Code et Nom correspondent aux colonnes SupplierID et Nom du fournisseur dans le fichier Excel des fournisseurs nettoyé et contenant les correspondances.  
  
 Un attribut basé sur un domaine est un attribut dont les valeurs sont remplies par les membres d'une autre entité. Les attributs basés sur un domaine empêchent les utilisateurs d'entrer des valeurs d'attribut qui ne sont pas valides. Une valeur d'attribut peut uniquement être sélectionnée dans la liste déroulante qui est remplie par une autre entité. Dans ce didacticiel, l'attribut État de l'entité Fournisseur est un attribut basé sur un domaine, avec les valeurs de l'entité État. Vous pouvez modifier la valeur de l'attribut État de l'entité Fournisseur uniquement par l'une des valeurs de l'entité État. Consultez [Attributs basés sur un domaine](../master-data-services/domain-based-attributes-master-data-services.md) pour plus de détails.  
  
 Une hiérarchie dérivée dans MDS est basée sur la relation de l'attribut basé sur un domaine qui existe dans le modèle. Dans ce didacticiel, vous allez créer une hiérarchie dérivée entre l'entité Fournisseur et l'entité État. Après avoir créé la hiérarchie dérivée, vous verrez la liste des États dans le navigateur de Master Data Manager. Lorsque vous cliquerez sur un État dans la liste, vous verrez les fournisseurs qui appartiennent à cet État dans le volet droit. Vous allez créer une hiérarchie dérivée basée sur cette relation ultérieurement. Consultez [Hiérarchies dérivées](../master-data-services/derived-hierarchies-master-data-services.md) pour plus de détails.  
  
 Vous avez créé une base de connaissances dans DQS et vous l'avez utilisée pour le nettoyage et la correspondance des données des fournisseurs, puis vous avez stocké les résultats dans le fichier Data.xls contenant les données des fournisseurs nettoyées et mises en correspondance. Dans cette leçon, vous allez télécharger les données nettoyées et mises en correspondance dans MDS. DQS contient uniquement les connaissances relatives aux données (métadonnées) alors que MDS stocke les données elles-mêmes (ensemble de référence). Exemple : DQS peut acquérir des connaissances sur plusieurs fournisseurs, mais MDS ne conserve que les fournisseurs qu’une société utilise.  
  
 Dans cette leçon, vous allez effectuer les tâches suivantes :  
  
1.  Créer le modèle **Fournisseurs** dans **MDS** à l'aide de l' **Application Web Master Data Manager Web Application**.  
  
2.  Ouvrir le fichier **Data.xls** contenant les données des fournisseurs nettoyées et mises en correspondance dans Excel et utiliser le **Complément MDS pour Excel** pour créer une entité appelée **Fournisseur** , puis téléchargez les données dans MDS.  
  
3.  Vérifier que les données sont créées dans MDS à l'aide de **Master Data Manager**.  
  
4.  Créer une entité nommée **État** et mettre à jour l'attribut **État** de l'entité **Fournisseur** pour qu'il s'agisse d'un attribut basé sur un domaine qui dépend de l'entité **État** . Pour cela, vous devez utiliser le **Complément MDS pour Excel**.  
  
5.  Vérifier que l'attribut basé sur un domaine est créé à l'aide de **Master Data Manager** et mettre à jour les valeurs de l'attribut **Nom** de l'entité **État** .  
  
6.  Afficher les mises à jour que vous avez effectuées à l'aide de **Master Data Manager** dans **Excel**.  
  
7.  Charger les valeurs de l'entité **État** dans **Excel** et ajouter une valeur, puis vérifier que l'ajout a été pris en compte à l'aide de **Master Data Manager**.  
  
8.  Créer et utiliser une hiérarchie dérivée à l'aide de la relation d'attribut basé sur un domaine entre l'entité **Fournisseur** et l'entité **État** (l'attribut État de l'entité Fournisseur est un type d'entité État) à l'aide de **Master Data Manager**.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 1 : Créer un modèle fournisseurs à l’aide de Master Data Manager](../../2014/tutorials/task-1-creating-suppliers-model-using-master-data-manager.md)  
  
  
