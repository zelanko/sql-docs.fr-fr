---
title: Définir l’analyse rapide | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: dcd1dc09-6eaf-440b-9ce6-fef779ff794f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e6ff2c6ecd536dd5ecc34dceb358ffcf578ff3a7
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85421726"
---
# <a name="set-fast-parse"></a>Définir l'analyse rapide
  La propriété d'analyse rapide doit être définie pour chaque colonne de la source ou de la transformation utilisant l'analyse rapide. Pour définir cette propriété, faites appel à l'éditeur avancé de la source de fichier plat et de la transformation de conversion de données.  
  
### <a name="to-set-fast-parse"></a>Pour définir l'analyse rapide  
  
1.  Cliquez avec le bouton droit sur la source de fichier plat ou sur la transformation de conversion de données, puis cliquez sur **Afficher l’éditeur avancé**.  
  
2.  Dans la boîte de dialogue **Éditeur avancé** , cliquez sur l'onglet **Propriétés d'entrée et de sortie** .  
  
3.  Dans le volet **Entrées et sorties** , cliquez sur la colonne pour laquelle vous souhaitez activer l'analyse rapide.  
  
4.  Dans le Fenêtre Propriétés, développez le nœud **propriétés personnalisées** , puis affectez à la propriété la valeur `FastParse` `True` .  
  
5.  Cliquez sur **OK**.  
  
  
