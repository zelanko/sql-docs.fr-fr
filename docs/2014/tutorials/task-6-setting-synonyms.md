---
title: 'Tâche 6 : définition des synonymes | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b7d35ee9-d1c9-41d9-bbc5-0ca7db93e54d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 4499a0a099c92a9b1802cc905da3d0a473808eeb
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177227"
---
# <a name="task-6-setting-synonyms"></a>Tâche 6 : Définition des synonymes
  Dans cette tâche, vous devez définir deux valeurs de domaine, **USA** et **États-Unis**, du domaine **Pays** comme synonymes, avec **États-Unis** comme valeur menante. Dans la mesure où l'option **Utiliser des valeurs menantes** a été sélectionnée lors de la création du domaine **Pays** , toutes les valeurs **USA** pour le domaine **Pays** seront remplacées par **États-Unis** (car États-Unis est la valeur menante). Consultez [Modifier les valeurs de domaine](https://msdn.microsoft.com/library/hh510408.aspx) pour plus de détails.

1.  Sélectionnez le domaine **Pays** dans la liste des domaines.

2.  Cliquez sur l'onglet **Valeurs du domaine** .

3.  Cliquez sur le bouton **Ajouter une valeur de domaine** de la barre d'outils.

4.  Tapez **USA** pour la valeur et appuyez sur **ENTRÉE**.

5.  Sélectionnez à la fois **États-Unis** et **USA** à l'aide de la touche CTRL ou de la touche MAJ, cliquez avec le bouton droit sur les éléments sélectionnés, puis cliquez sur **Définir en tant que synonyme**. DQS regroupe ces valeurs et désigne l'une des valeurs comme valeur menante par laquelle les autres seront remplacées.

     ![Menu Définir en tant que synonyme](../../2014/tutorials/media/et-settingsynonyms-01.jpg "Menu Définir en tant que synonyme")

6.  Notez que **États-Unis** est défini comme valeur menante. Si vous souhaitez que USA soit la valeur menante, cliquez avec le bouton droit sur USA et sélectionnez l'option **Définir en tant que valeur menante** . Pour ce didacticiel, nous utiliserons **États-Unis** comme valeur menante.

     ![United States et USA comme synonymes](../../2014/tutorials/media/et-settingsynonyms-02.jpg "United States et USA comme synonymes")

## <a name="next-step"></a>étape suivante
 [Tâche 7 : Création d'une règle de domaine composite](../../2014/tutorials/task-7-creating-a-composite-domain.md)


