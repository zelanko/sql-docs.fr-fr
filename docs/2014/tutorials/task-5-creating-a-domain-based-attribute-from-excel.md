---
title: 'Tâche 5 : Création d’un attribut basé sur un domaine à partir d’Excel | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 07cbc624-2c6b-4568-96e4-f18663a05d80
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8c4b2ae49de561dd7a82785bda955d6701abc770
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37251281"
---
# <a name="task-5-creating-a-domain-based-attribute-from-excel"></a>Tâche 5 : Créer un attribut basé sur un domaine à partir d'Excel
  Dans cette tâche, vous convertissez le **état** attribut de la **fournisseur** entité en tant qu’un **attribut basé sur un domaine**. Après avoir configuré l’attribut d’état pour être basés sur un domaine et le publier dans MDS, une nouvelle entité appelée **état** va être créé sur le serveur MDS avec toutes les valeurs dans la colonne et le **état** attribut de la **Fournisseur** entité sera remplie avec les valeurs à partir de la **état** entité. À présent, le **fournisseurs** modèle doit avoir deux entités : **fournisseur** et **état** où le **état** attribut de la  **Fournisseur** entité est un attribut basé sur le domaine qui dépend de **état** entité.  
  
1.  Basculez vers **Excel** fenêtre a **Cleansed and Matched Suppliers.xlsx** ouvrir.  
  
2.  Cliquez sur **Actualiser** bouton sur le ruban pour obtenir les dernières mises à jour à partir de MDS. Si vous avez effectué le paramètre facultatif, vous devez voir les deux enregistrements plus **tâche 4**.  
  
3.  Cliquez sur le nom de la colonne **état** (cellule **I1**) dans le **ligne d’en-tête**.  
  
     ![Excel - bouton Propriétés d’attributs](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-01.jpg "Excel - bouton Propriétés d’attributs")  
  
4.  Cliquez sur **propriétés d’attribut** sur le ruban.  
  
5.  Dans le **propriétés d’attribut** boîte de dialogue, sélectionnez **liste contrainte (basée sur le domaine)** pour le **type d’attribut**.  
  
6.  Type **état** pour le **nouveau nom d’entité** et cliquez sur **OK**.  
  
     ![Excel - boîte de dialogue de propriétés attribut](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-02.jpg "Excel - boîte de dialogue de propriétés attribut")  
  
7.  Maintenant, dans Excel, vous devez voir **flèche vers le bas** lorsque vous cliquez sur n’importe quelle valeur dans la **état** colonne. Modifiez la valeur à l'aide de la liste déroulante, le cas échéant.  
  
     ![Excel - liste déroulante liste avec les états](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-03.jpg "Excel - liste déroulante liste des États")  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 6 : Vérification que l’attribut basé sur un domaine est créé à l’aide de Master Data Manager](../../2014/tutorials/task-6-verify-domain-based-attribute-master-data-manager.md)  
  
  
