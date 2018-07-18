---
title: Advanced éditeur de requête d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 27e7fc46-689d-43a4-9647-1c27d182bdd6
caps.latest.revision: 9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 75347810fafa87828dd09653059e9a403a1892ef
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167670"
---
# <a name="advanced-data-mining-query-editor"></a>Éditeur de requête d’exploration de données données avancées
  Le **données d’exploration de données éditeur de requêtes avancé** est un outil pour vous aider à créer des requêtes et des modèles personnalisés.  
  
 L'éditeur fournit un ensemble de modèles avec des liens interactifs. Cliquez simplement sur chaque lien, puis utilisez les boîtes de dialogue pour sélectionner des objets ou des valeurs et générer des instructions DMX (Data Mining Extensions) complexes. Basculez la vue vers le modèle d'édition de texte pour modifier l'instruction DMX manuellement.  
  
 Pour accéder à la **données d’exploration de données éditeur de requêtes avancé**, cliquez sur **requête** puis cliquez sur **avancé**.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Volet requête DMX**  
 L'instruction DMX active s'affiche.  
  
 Cliquez avec le bouton droit sur le volet pour copier l'instruction DMX active.  
  
 Cliquez sur une partie sélectionnée de l'instruction pour obtenir des options spécifiques à cette clause. Par exemple, pour supprimer, ajouter ou modifier la sortie, cliquez sur le  **\<sortie >** lien.  
  
 **Modifier la requête/Générateur de requêtes**  
 Utilisez ce bouton pour basculer l’éditeur entre un éditeur de texte, où vous pouvez écrire des instructions DMX directement ; et le **Générateur de requêtes**, qui vous aide à vous générez une instruction DMX.  
  
> [!NOTE]  
>  **Avertissement :** si vous changez de vue avant l’exécution de la requête, un message s’affiche indiquant que vous risquez de perdre certaines modifications. Si l’instruction DMX est valide, dans de nombreux cas le **Générateur de requêtes** convertit correctement ces modifications. Toutefois, si vous avez généré une instruction DMX particulièrement complexe, vous devez enregistrer votre travail avant de changer de vue.  
  
 **Modèles DMX**  
 Cliquez et sélectionnez à partir d'une liste de modèles qui contient des exemples DMX. Les modèles fournissent tous les types de modèle ou requête de prédiction nécessaires, notamment les requêtes qui utilisent des tables imbriquées, et les instructions DMX pour gérer des modèles. Même si vous connaissez certaines instructions DMX, les modèles permettent de gagner du temps en obtenant la syntaxe correcte.  
  
 **Choisissez le modèle**  
 Cliquez pour afficher la liste des modèles d'exploration de données disponibles sur la connexion actuelle.  
  
 Vous pouvez également afficher une liste des modèles disponibles en cliquant sur le nom du modèle dans l’instruction DMX dans le **requête DMX** volet. Le nom du modèle est généralement surligné en rouge.  
  
 **Sélectionnez l’entrée**  
 Cliquez pour sélectionner les données à utiliser comme entrée dans le modèle d'exploration de données. Si aucune source de données n’a été spécifiée, vous pouvez également cliquer sur le  **\<entrée >** link, ce qui est mis en surbrillance en rouge dans le **requête DMX** volet.  
  
 Sélectionnez **@InputRowset** dans la liste déroulante pour ouvrir le **remplacer InputRowset** boîte de dialogue zone et de modifier une entrée existante.  
  
 Sélectionnez **ajouter une entrée** pour ouvrir le **ajouter une entrée** boîte de dialogue zone, puis spécifiez une nouvelle source de données.  
  
 Vous pouvez également modifier une entrée existante en cliquant sur le **@InputRowset** link, ce qui est mis en surbrillance en rouge dans le volet requête DMX.  
  
 **Mapper des colonnes**  
 Sélectionnez des colonnes dans le modèle d'exploration de données et mappez-les aux colonnes de la source de données externe.  
  
 Vous pouvez également cliquer sur la mise en surbrillance  **\<mappage >** lien dans le volet requête DMX.  
  
 **Ajouter une sortie**  
 Cliquez pour sélectionner les colonnes qui correspondent à la sortie dans la requête de prédiction.  
  
 Vous pouvez également cliquer sur la mise en surbrillance  **\<ajouter une sortie >** lien dans le volet requête DMX.  
  
 **Colonnes du modèle**  
 Répertorie les colonnes du modèle d'exploration de données sélectionné. Une marque en forme de losange en regard du nom de la colonne indique que celle-ci est une colonne prévisible.  
  
 **Colonnes d'entrée**  
 Répertorie les colonnes issues de la source de données externes ajoutées comme entrées.  
  
## <a name="see-also"></a>Voir aussi  
 [Requête &#40;compléments d’exploration de données SQL Server&#41;](query-sql-server-data-mining-add-ins.md)  
  
  
