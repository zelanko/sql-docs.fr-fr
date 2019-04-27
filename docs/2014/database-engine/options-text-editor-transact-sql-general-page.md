---
title: Options (éditeur de texte - Page de Transact-SQL-général) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.General
dev_langs:
- TSQL
ms.assetid: 7021ecb7-8fb5-4d8c-b984-3d34fcde8be2
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 28559b6037fa6b0e95bb6748f85d3d0cecd2df8b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62774163"
---
# <a name="options-text-editor---transact-sql--general-page"></a>Options (éditeur de texte - Page de Transact-SQL-général)
  Utilisez la boîte de dialogue d’options **Général** pour modifier le comportement d’édition général de l’Éditeur de requête [!INCLUDE[ssDE](../includes/ssde-md.md)], qui permet de modifier des scripts [!INCLUDE[tsql](../includes/tsql-md.md)]. Pour afficher ces paramètres, cliquez sur **Options** dans le menu **Outils**, développez le sous-dossier **Transact-SQL**, puis cliquez sur **Général**.  
  
## <a name="setting-options-in-multiple-locations"></a>Définition d'options en plusieurs emplacements  
 Les options de l’Éditeur de requête [!INCLUDE[ssDE](../includes/ssde-md.md)] peuvent également être définies dans la boîte de dialogue **Tous les langages Général**. Si vous utilisez les boîtes de dialogue **Tous les langages** pour définir des options différentes pour les autres éditeurs [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], comme les éditeurs DMX ou MDX, vous devez réinitialiser les options de l’Éditeur de requête [!INCLUDE[ssDE](../includes/ssde-md.md)] à l’aide de cette boîte de dialogue.  
  
## <a name="statement-completion"></a>Compléter automatiquement les instructions  
 **Répertorier automatiquement les membres**  
 Lorsque cette case à cocher est activée, des listes d'objets de base de données et de schéma, de colonnes, de fonctions table ou de fonctions disponibles sont affichées au fur et à mesure que vous tapez dans l'éditeur. Sélectionnez un élément dans la liste contextuelle pour l'insérer dans votre code.  
  
 **Masquer les membres avancés**  
 Cette case à cocher n'est pas disponible.  
  
 **Informations sur les paramètres**  
 Lorsque cette case à cocher est activée, les informations de paramètres sont affichées pour une procédure stockée ou une fonction située juste à gauche du point d'insertion (curseur). Les informations incluent une liste des paramètres disponibles avec leurs noms et types de données.  
  
## <a name="settings"></a>Paramètres  
 **Activer l’espace virtuel**  
 Lorsque cette case à cocher est activée, vous pouvez cliquer au-delà de la fin d'une ligne de code et taper du texte. Activez cette case à cocher pour placer des commentaires à un point cohérent, en regard de votre code. Activer cette case à cocher désactive la case à cocher **Retour automatique à la ligne**.  
  
 **Le retour automatique à**  
 Lorsque cette case à cocher est activée, toute partie d'une ligne qui s'étend horizontalement au-delà de la zone visible de l'éditeur est affichée automatiquement à la ligne suivante. Cocher cette case coche la case **Afficher des glyphes visuels pour le retour automatique à la ligne** et décoche la case **Activer l’espace virtuel**.  
  
 **Afficher des glyphes visuels pour le retour automatique à**  
 Lorsque cette case à cocher est activée, une flèche retour est affichée si une ligne longue nécessite un retour automatique à la ligne suivante.  
  
 **Appliquer les commandes Couper ou copier aux lignes vides lors de l’absence de sélection**  
 Cette case à cocher définit le comportement de l'éditeur lorsque vous placez le point d'insertion sur une ligne vide, n'effectuez aucune sélection et cliquez sur **Copier** ou **Couper**.  
  
 Lorsque cette case à cocher est activée, la ligne vide est copiée ou coupée. Si vous cliquez ensuite sur **Coller**, une nouvelle ligne vide est insérée.  
  
 Lorsque cette case à cocher est désactivée, aucun élément n'est copié ou coupé. Si vous cliquez ensuite sur **Coller**, le dernier contenu copié est collé. Si aucune sélection n'a été copiée précédemment, aucune sélection n'est collée.  
  
 Ce paramètre n'a aucun effet sur les commandes **Copier** ou **Couper** lorsqu'une ligne n'est pas vide. Si aucun élément n'est sélectionné, la totalité de la ligne est copiée ou coupée. Si vous cliquez ensuite sur **Coller**, le texte de la totalité de la ligne et son caractère de fin de ligne sont collés.  
  
## <a name="display"></a>Afficher  
 **Numéros de ligne**  
 Lorsque cette case à cocher est activée, un numéro de ligne est affiché en regard de chaque ligne de code.  
  
> [!NOTE]  
>  Ces numéros de ligne ne sont pas ajoutés à votre code et ne s'impriment pas. Ils servent de référence uniquement.  
  
 **Activer la navigation dans les URL simple clic**  
 Lorsque cette case à cocher est activée, le curseur est remplacé par une main avec un doigt tendu lorsqu'il passe sur une URL dans l'éditeur. Vous pouvez alors cliquer sur l'URL pour afficher la page correspondante dans votre navigateur Web.  
  
 **Barre de navigation**  
 Cette case à cocher n'est pas disponible.  
  
  
