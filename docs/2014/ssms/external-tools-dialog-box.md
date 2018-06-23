---
title: Outils externes, boîte de dialogue | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adding external tools
- external tools [SQL Server Management Studio]
- SQL Server Management Studio [SQL Server], external tools
ms.assetid: ba797203-24d0-4922-9b97-8ab483f1db14
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 15d26c23413cc3f47cba2cce5d7d7ce9efab9a66
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155171"
---
# <a name="external-tools-dialog-box"></a>Boîte de dialogue Outils externes
  Utilisez la boîte de dialogue **Outils externes** pour ajouter des outils externes tels que SQLCMD ou le Bloc-notes au menu **Outils**. L'ajout d'outils externes vous permet de lancer facilement d'autres applications tout en travaillant dans l'environnement [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] . Vous pouvez spécifier des arguments et un répertoire de travail lors du lancement de l'outil. En outre, la sortie de certains outils peut être affichée dans la fenêtre **Sortie** . La boîte de dialogue **Outils externes** est accessible via le menu **Outils** .  
  
## <a name="options"></a>Options  
 **Sommaire du menu**  
 Répertorie les titres des éléments ajoutés au menu **Outils** . Utilisez les flèches **Monter** et **Descendre** pour modifier l'ordre d'apparition des éléments dans le menu. Utilisez le bouton **Supprimer** pour supprimer un élément du menu.  
  
 **Monter**  
 Déplace l'outil sélectionné vers le haut de la liste des outils qui apparaissent dans le menu **Outils** .  
  
 **Descendre**  
 Déplace l'outil sélectionné vers le bas de la liste des outils qui apparaissent dans le menu **Outils** .  
  
 **Ajouter**  
 Vide les zones de texte pour que vous puissiez spécifier un nouvel outil.  
  
 **Supprimer**  
 Supprime l'outil ou la commande de la liste **Contenu du menu** , ainsi que du menu **Outils** .  
  
 **Titre**  
 Entrez le nom sous lequel l'outil ou la commande sera affiché dans le sous-menu **Outils externes** du menu **Outils** . Faites précéder une des lettres de ce nom du caractère & pour la définir comme touche de raccourci de l'outil. Par exemple, « &SQLCMD » s'afficherait sous la forme SQLCMD dans le menu **Outils**.  
  
 **Commande**  
 Spécifiez le chemin d'accès au fichier à lancer.  
  
 **Arguments**  
 Spécifiez les variables qui sont passées à l'outil lorsque celui-ci est sélectionné dans le menu. Les arguments peuvent spécifier des valeurs qui sont passées à l'outil ou à la commande au moment de son lancement. Par exemple, une valeur peut spécifier un nom de fichier ou un répertoire. Utilisez le bouton fléché pour faire votre sélection dans une liste d'arguments prédéfinis. Vous pouvez en ajouter plusieurs. Pour obtenir la liste complète des arguments prédéfinis et leur définition, consultez [Arguments for External Tools](menu-help/external-tools.md). Vous pouvez entrer également des arguments personnalisés, par exemple, des commutateurs de ligne de commande, selon la commande ou l'outil utilisé.  
  
 **Utiliser la fenêtre de sortie**  
 Ouvre la fenêtre de sortie [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] pour afficher la sortie de la commande en cours d'exécution. Tous les outils ne présentent pas de sortie dans un format affichable dans la fenêtre Sortie. Pour plus d’informations, consultez [Fenêtre Sortie](../relational-databases/scripting/transact-sql-debugger-output-window.md).  
  
 **Considérer la sortie en Unicode**  
 Interprète la sortie comme Unicode.  
  
 **Répertoire initial**  
 Spécifie le répertoire de travail de l'outil. Utilisez le bouton fléché pour sélectionner des répertoires. Vous pouvez en sélectionner plusieurs.  
  
 **Demander les arguments**  
 Affiche la boîte de dialogue **Arguments** pour vous permettre d'entrer ou de modifier des valeurs pour les arguments chaque fois que vous lancez l'outil externe.  
  
 **Fermer en quittant**  
 Ferme en même temps que l'outil la fenêtre qu'il a ouverte.  
  
## <a name="example"></a>Exemple  
 La saisie des valeurs suivantes dans la boîte de dialogue **Outils externes** crée un élément de menu libellé « DAC » qui, une fois sélectionné, ouvre une invite de commandes et exécute l'utilitaire **sqlcmd** à l'aide de la connexion administrateur dédiée.  
  
|Zone|Valeur|  
|---------|-----------|  
|**Title**|DAC|  
|**Commande**|[!INCLUDE[ssInstallPath](../includes/ssinstallpath-md.md)]Tools\Binn\SQLCMD.exe|  
|**Arguments**|-A|  
  
## <a name="see-also"></a>Voir aussi  
 [Arguments des outils externes](menu-help/external-tools.md)   
 [Éléments généraux de l’interface utilisateur](general-user-interface-elements.md)  
  
  