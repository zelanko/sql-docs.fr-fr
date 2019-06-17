---
title: Ajouter un sous-rapport et des paramètres (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10093"
- sql12.rtp.rptdesigner.subreportproperties.general.f1
ms.assetid: 94f960f8-a629-4f1e-8277-c3b8f0680d98
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 906f4527bdca38f4571a2e1686f885a2857e47c3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66106780"
---
# <a name="add-a-subreport-and-parameters-report-builder-and-ssrs"></a>Ajouter un sous-rapport et des paramètres (Générateur de rapports et SSRS)
  Ajoutez des sous-rapports à un rapport pour créer un rapport principal servant de conteneur à plusieurs rapports connexes. Un sous-rapport est une référence à un autre rapport. Pour connecter les rapports par des valeurs de données (par exemple, pour que plusieurs rapports indiquent des données pour le même client), vous devez désigner un rapport paramétrable (par exemple, un rapport qui affiche les renseignements concernant un client spécifique) en tant que sous-rapport. Lorsque vous ajoutez un sous-rapport au rapport principal, vous pouvez spécifier des paramètres à passer au sous-rapport.  
  
 Vous pouvez aussi ajouter des sous-rapports aux lignes ou colonnes dynamiques d'une table ou d'une matrice. Lorsque le rapport principal est traité, le sous-rapport est traité pour chaque ligne. Dans ce cas, demandez-vous si vous pouvez obtenir le résultat escompté en utilisant des régions de données classiques ou imbriquées.  
  
 Pour ajouter un sous-rapport à un rapport, vous devez d'abord créer le rapport qui sert de sous-rapport. Pour plus d’informations sur la création du sous-rapport, consultez [Sous-rapports &#40;Générateur de rapports et SSRS&#41;](subreports-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-subreport"></a>Pour ajouter un sous-rapport  
  
1.  Sous l’onglet **Insérer** , cliquez sur **Sous-rapport**.  
  
2.  Sur l'aire de conception, cliquez à un endroit quelconque du rapport et faites glisser la souris pour créer une zone de la taille voulue pour le sous-rapport. Une autre solution consiste à cliquer sur l'aire de conception pour créer un sous-rapport de taille par défaut.  
  
3.  Cliquez avec le bouton droit sur le sous-rapport, puis cliquez sur **Propriétés du sous-rapport**.  
  
4.  Dans la boîte de dialogue **Propriétés du sous-rapport** , tapez un nom dans la zone de texte **Nom** ou acceptez le nom par défaut. Ce nom doit être unique dans le rapport. Par défaut, un nom général, tel que Subreport1 ou Subreport2, est assigné.  
  
5.  Dans la zone **Utiliser ce rapport comme sous-rapport** , cliquez sur **Parcourir**ou tapez le nom du rapport. Il est préférable de cliquer sur **Parcourir** , car le chemin du sous-rapport est spécifié automatiquement. Vous pouvez spécifier le rapport de plusieurs manières. Pour plus d’informations, consultez [Spécification de chemins d’accès à des éléments externes &#40;Générateur de rapports et SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).  
  
6.  (Facultatif) Cliquez sur **Oui** pour **Omettre la bordure sur le saut de page** et ainsi empêcher l’affichage d’une bordure au milieu du sous-rapport si ce dernier prend plusieurs pages.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-specify-parameters-to-pass-to-a-subreport"></a>Pour spécifier les paramètres à passer à un sous-rapport  
  
1.  En mode Conception, cliquez avec le bouton droit sur le sous-rapport, puis cliquez sur **Propriétés du sous-rapport**.  
  
2.  Dans la boîte de dialogue **Propriétés du sous-rapport** , cliquez sur **Paramètres**.  
  
3.  Cliquez sur **Ajouter**. Une nouvelle ligne est ajoutée à la grille des paramètres.  
  
4.  Dans la zone **Nom** , tapez le nom d’un paramètre du sous-rapport ou choisissez-le dans la zone de liste. Ce nom doit correspondre au nom d'un paramètre de rapport, pas d'un paramètre de requête, dans le sous-rapport.  
  
5.  Dans la zone de liste **Valeur** , tapez ou sélectionnez une valeur à passer au sous-rapport. Cette valeur peut être du texte statique ou une expression qui fait référence à un champ ou un autre objet situé dans le rapport principal.  
  
    > [!NOTE]  
    >  Dans le Générateur de rapports, s’il manque un paramètre dans la liste **Paramètres** et qu’une valeur par défaut est définie pour le sous-rapport, celui-ci est traité correctement.  
    >   
    >  Dans le Générateur de rapports, tous les paramètres nécessaires au sous-rapport doivent figurer dans la liste **Paramètres** . S'il manque un paramètre obligatoire, le sous-rapport ne s'affiche pas correctement dans le rapport principal.  
  
6.  Répétez les étapes 3 et 5 pour spécifier un nom et une valeur pour chaque paramètre de sous-rapport.  
  
7.  Pour supprimer un paramètre du sous-rapport, cliquez sur le paramètre dans la grille de paramètres, puis cliquez sur **Supprimer**.  
  
8.  Pour modifier l'ordre d'un paramètre de sous-rapport, cliquez sur le paramètre, puis cliquez sur le bouton Haut ou Bas.  
  
     La modification de l'ordre d'un paramètre n'a aucun effet sur le traitement du sous-rapport.  
  
## <a name="see-also"></a>Voir aussi  
 [Sous-rapports &#40;Générateur de rapports et SSRS&#41;](subreports-report-builder-and-ssrs.md)   
 [Comportements de rendu &#40;Générateur de rapports et SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md)  
  
  
