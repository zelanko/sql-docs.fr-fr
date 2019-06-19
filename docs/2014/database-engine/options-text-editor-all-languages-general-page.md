---
title: Options (Page Général de l’éditeur de texte - toutes les langues -) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: bf18907c-94e2-4c09-9b2b-0925ac04c627
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 385380e6e51c3b8519e7dbc6ec3d934e1ef14846
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66089248"
---
# <a name="options-text-editor---all-languages---general-page"></a>Options (Éditeur de texte - Toutes les langues - Page Général)
  Cette boîte de dialogue vous permet de définir les options d'édition générales des cinq éditeurs de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Pour afficher ces options, sélectionnez **Options** dans le menu **Outils** . Sélectionnez le dossier **Éditeur de texte**, développez le dossier **Tous les langages**, puis cliquez sur **Général**.  
  
## <a name="option-settings-by-editor"></a>Paramètres d'option par éditeur  
 Vous devez utilisez les boîtes de dialogue **Tous les langages** pour définir les options des éditeurs DMX, MDX et SQL Server Compact. Les options définies ici s'appliquent aussi aux éditeurs de texte brut, Transact-SQL et XML, mais vous pouvez définir les options de ces éditeurs séparément en développant les sous-dossiers de ces langages et en sélectionnant leur page d'options.  
  
> [!CAUTION]  
>  Si vous définissez une option à l’aide de cette boîte de dialogue, mais que vous voulez un paramétrage différent pour les éditeurs de texte brut, Transact-SQL ou XML, vous devrez définir les options de ces éditeurs après avoir appliqué les sélections effectuées dans la boîte de dialogue **Tous les langages**.  
  
 Certains éditeurs peuvent ne pas prendre en charge toutes les options répertoriées dans cette page. Une coche ombrée est affichée lorsqu’une option a été sélectionnée dans la page **Général** de la boîte de dialogue **Options** pour certains langages de programmation, mais pas pour d’autres.  
  
## <a name="statement-completion"></a>Compléter automatiquement les instructions  
 **Répertorier automatiquement les membres**  
 Affiche les listes contextuelles des membres, des propriétés ou des valeurs disponibles lorsque vous faites des entrées dans l'éditeur. Sélectionnez un élément dans la liste contextuelle pour l'insérer dans votre code. En cochant cette case, vous activez l’option **Masquer les membres avancés**.  
  
 **Masquer les membres avancés**  
 Raccourcit les listes contextuelles de saisie semi-automatique des instructions, en affichant uniquement les éléments les plus couramment utilisés. D'autres éléments sont filtrés dans la liste. Cette option n'est pas disponible si aucun membre n'est désigné comme membre avancé.  
  
 **Informations sur les paramètres**  
 Affiche la syntaxe complète de la déclaration ou de la procédure active à gauche du point d'insertion dans l'éditeur, avec tous les paramètres disponibles. Le paramètre suivant qui peut être affecté est affiché en gras.  
  
## <a name="settings"></a>Paramètres  
 **Activer l’espace virtuel**  
 Place des commentaires dans un emplacement cohérent à côté de votre code. Lorsque cette case à cochée est activée, vous pouvez placer le curseur au-delà du dernier caractère de la ligne. Lorsque vous effectuez des saisies, les tabulations ou les espaces sont automatiquement ajoutés pour terminer la ligne au niveau du point d'insertion.  
  
 **Le retour automatique à**  
 Permet d'afficher à la ligne suivante toute partie d'une ligne qui s'étend horizontalement au-delà de la zone visible de l'éditeur. L'activation de cette case à cocher active l'option **Afficher des glyphes visuels pour le retour automatique à la ligne** .  
  
 **Afficher des glyphes visuels pour le retour automatique à**  
 Permet d'afficher une flèche retour quand une ligne nécessite un retour automatique à la ligne suivante.  
  
> [!NOTE]  
>  Ces flèches de rappel ne sont pas ajoutées à votre code et ne s'impriment pas. Ils servent de référence uniquement. Cette fonctionnalité n'est pas disponible dans tous les types d'éditeurs.  
  
 **Appliquer les commandes Couper ou copier aux lignes vides lors de l’absence de sélection**  
 Permet de définir le comportement de l'éditeur lorsque vous placez le point d'insertion sur une ligne vide, n'effectuez aucune sélection et cliquez sur **Copier** ou **Couper**.  
  
 Lorsque cette case à cocher est activée, la ligne vide est copiée ou coupée. Si vous cliquez ensuite sur **Coller**, une nouvelle ligne vide est insérée.  
  
 Lorsque cette case à cocher est désactivée, aucun élément n'est copié ou coupé. Si vous cliquez ensuite sur **Coller**, le dernier contenu copié est collé. Si aucun élément n'a été copié, aucun élément n'est collé.  
  
 Ce paramètre n’a aucun effet sur la commande **Copier** ou **Couper** lorsqu’une ligne n’est pas vide. Si aucun élément n'est sélectionné, la totalité de la ligne est copiée ou coupée. Si vous cliquez ensuite sur **Coller**, le texte de la totalité de la ligne et son caractère de fin de ligne sont collés.  
  
## <a name="display"></a>Afficher  
 **Numéros de ligne**  
 Permet d'afficher un numéro de ligne en regard de chaque ligne de code.  
  
> [!NOTE]  
>  Ces numéros de ligne ne sont pas ajoutés à votre code et ne s'impriment pas. Ils servent de référence uniquement.  
  
 **Activer la navigation dans les URL simple clic**  
 Permet de remplacer le curseur par une main avec un doigt tendu lorsqu'il passe sur une URL dans l'éditeur. Vous pouvez alors cliquer sur l'URL pour afficher la page correspondante dans votre navigateur Web.  
  
 **Barre de navigation**  
 Affiche une barre de navigation en haut de l'éditeur de code. Utilisez ses listes déroulantes **Objets** et **Procédures** pour choisir un objet particulier dans votre code, effectuer une sélection à partir de ses procédures et insérer une instance de la procédure sélectionnée. La barre de navigation n’est pas disponible pour tous les types de code.  
  
  
