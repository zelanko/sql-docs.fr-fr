---
title: Créer et gérer des Perspectives (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.perspectivedb.f1
ms.assetid: 2a411c2b-2820-4086-ad7f-ce6a941fefc7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 25f8de0649f82abbcc6ceb4ac6a92844de04b4b7
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52502282"
---
# <a name="create-and-manage-perspectives-ssas-tabular"></a>Créer et gérer des perspectives (SSAS Tabulaire)
  Les perspectives définissent des sous-ensembles visualisables d'un modèle et des points de vue du modèle focalisés sur un domaine d'activité ou sur une application. Les tâches de cette rubrique décrivent comment créer et gérer des perspectives à l'aide de la boîte de dialogue **Perspectives** dans le générateur de modèles.  
  
 Cette rubrique inclut les tâches suivantes :  
  
-   [Pour ajouter une perspective](#bkmk_add)  
  
-   [Pour modifier une perspective](#bkmk_edit)  
  
-   [Pour renommer une perspective](#bkmk_rename)  
  
-   [Pour supprimer une perspective](#bkmk_delete)  
  
-   [Pour copier une perspective](#bkmk_copy)  
  
## <a name="tasks"></a>Tâches  
 Pour créer des perspectives, vous allez utiliser la boîte de dialogue **Perspectives** , dans laquelle vous pouvez ajouter, modifier, supprimer, copier et afficher des perspectives. Pour consulter la boîte de dialogue **Perspectives** , dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cliquez sur le menu **Modèle** , puis sur **Perspectives**.  
  
###  <a name="bkmk_add"></a> Pour ajouter une perspective  
  
-   Pour ajouter une nouvelle perspective, cliquez sur **Nouvelle perspective**. Vous pouvez ensuite activer et désactiver les objets de champ de votre choix pour les inclure ou les exclure et ensuite donner un nom à la nouvelle perspective.  
  
     Si vous créez une perspective vide avec tous les champs d'objet, un utilisateur utilisant cette perspective verra une liste de champs vide. Les perspectives doivent contenir au moins une table et une colonne.  
  
###  <a name="bkmk_edit"></a> Pour modifier une perspective  
  
-   Pour modifier une perspective, activez et désactivez les champs de colonne de la perspective, qui ajoute et supprime des objets de champ de la perspective.  
  
###  <a name="bkmk_rename"></a> Pour renommer une perspective  
  
-   Lorsque vous pointez sur l’en-tête de colonne d’une perspective (le nom de la perspective), le **renommer** bouton s’affiche. Pour renommer la perspective, cliquez sur **Renommer**, puis entrez un nouveau nom ou modifiez le nom existant.  
  
###  <a name="bkmk_delete"></a> Pour supprimer une perspective  
  
-   Lorsque vous pointez sur l’en-tête de colonne d’une perspective (le nom de la perspective), le **supprimer** bouton s’affiche. Pour supprimer la perspective, cliquez sur le bouton **Supprimer** , puis cliquez sur **Oui** dans la fenêtre de confirmation.  
  
###  <a name="bkmk_copy"></a> Pour copier une perspective  
  
-   Lorsque vous pointez sur un en-tête de colonne perspective, le **copie** bouton s’affiche. Pour créer une copie de cette perspective, cliquez sur le bouton **Copier** . Une copie de la perspective sélectionnée est ajoutée en tant que nouvelle perspective à droite des perspectives existantes. La nouvelle perspective hérite du nom de la perspective copiée et une annotation *- Copier* est ajoutée à la fin du nom. Par exemple, si une copie de la *Sales* perspective est créée, la nouvelle perspective est appelée *ventes - copie*.  
  
## <a name="see-also"></a>Voir aussi  
 [Perspectives &#40;SSAS Tabulaire&#41;](perspectives-ssas-tabular.md)   
 [Hiérarchies &#40;SSAS Tabulaire&#41;](hierarchies-ssas-tabular.md)  
  
  
