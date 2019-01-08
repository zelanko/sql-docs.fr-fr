---
title: Créer et gérer des perspectives dans les modèles tabulaires Analysis Services | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 962b6b90de6d95107d1a4cdd3484a44205afb630
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53071846"
---
# <a name="create-and-manage-perspectives"></a>Créer et gérer des perspectives 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Les perspectives définissent des sous-ensembles visualisables d'un modèle et des points de vue du modèle focalisés sur un domaine d'activité ou sur une application. Les tâches de cette rubrique décrivent comment créer et gérer des perspectives à l'aide de la boîte de dialogue **Perspectives** dans le générateur de modèles.  
  
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
 [Perspectives](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Hierarchies](../../analysis-services/tabular-models/hierarchies-ssas-tabular.md)  
  
  
