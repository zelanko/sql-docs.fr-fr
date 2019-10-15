---
title: Éditeur de requête d’exploration de données avancé | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 27e7fc46-689d-43a4-9647-1c27d182bdd6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4973ea427cea99d6e3c4527e8686e322a97efe48
ms.sourcegitcommit: c7a202af70fd16467a498688d59637d7d0b3d1f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72313610"
---
# <a name="advanced-data-mining-query-editor"></a>Éditeur de requêtes d’exploration de données avancée
  La **éditeur avancé requête d’exploration de données** est un outil qui vous aide à créer des modèles et des requêtes personnalisés.  
  
 L'éditeur fournit un ensemble de modèles avec des liens interactifs. Cliquez simplement sur chaque lien, puis utilisez les boîtes de dialogue pour sélectionner des objets ou des valeurs et générer des instructions DMX (Data Mining Extensions) complexes. Basculez la vue vers le modèle d'édition de texte pour modifier l'instruction DMX manuellement.  
  
 Pour accéder à la **éditeur avancé de requête d’exploration de données**, cliquez sur **requête** , puis sur **avancé**.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Volet requête DMX**  
 L'instruction DMX active s'affiche.  
  
 Cliquez avec le bouton droit sur le volet pour copier l'instruction DMX active.  
  
 Cliquez sur une partie sélectionnée de l'instruction pour obtenir des options spécifiques à cette clause. Par exemple, pour supprimer, ajouter ou modifier une sortie, cliquez avec le bouton droit sur le lien **\<Output >** .  
  
 **Modifier la requête/Générateur de requêtes**  
 Utilisez ce bouton pour basculer l’éditeur entre un éditeur de texte, dans lequel vous pouvez écrire des instructions DMX directement. et le **Générateur de requêtes**, qui vous aide à générer une instruction DMX.  
  
> [!NOTE]  
>  **Avertissement :** Si vous changez de vue avant l’exécution de la requête, un message s’affiche indiquant que vous risquez de perdre certaines modifications. Si l’instruction DMX est valide, dans de nombreux cas, l' **Générateur de requêtes** peut convertir correctement ces modifications. Toutefois, si vous avez généré une instruction DMX particulièrement complexe, vous devez enregistrer votre travail avant de changer de vue.  
  
 **Modèles DMX**  
 Cliquez et sélectionnez à partir d'une liste de modèles qui contient des exemples DMX. Les modèles fournissent tous les types de modèle ou requête de prédiction nécessaires, notamment les requêtes qui utilisent des tables imbriquées, et les instructions DMX pour gérer des modèles. Même si vous connaissez certaines instructions DMX, les modèles permettent de gagner du temps en obtenant la syntaxe correcte.  
  
 **Choisir un modèle**  
 Cliquez pour afficher la liste des modèles d'exploration de données disponibles sur la connexion actuelle.  
  
 Vous pouvez également afficher une liste des modèles disponibles en cliquant sur le nom du modèle dans l’instruction DMX dans le volet **requête DMX** . Le nom du modèle est généralement surligné en rouge.  
  
 **Sélectionner l’entrée**  
 Cliquez pour sélectionner les données à utiliser comme entrée dans le modèle d'exploration de données. Si aucune source de données n’a été spécifiée, vous pouvez également cliquer sur le lien **\<Input >** , qui est mis en surbrillance en rouge dans le volet **requête DMX** .  
  
 Sélectionnez **\@InputRowset** dans la liste déroulante pour ouvrir la boîte de dialogue **remplacer InputRowset** et modifier une entrée existante.  
  
 Sélectionnez **Ajouter une entrée** pour ouvrir la boîte de dialogue **Ajouter une entrée** et spécifier une nouvelle source de données.  
  
 Vous pouvez également modifier une entrée existante en cliquant sur le lien **\@InputRowset** , qui est mis en surbrillance en rouge dans le volet requête DMX.  
  
 **Mapper les colonnes**  
 Sélectionnez des colonnes dans le modèle d'exploration de données et mappez-les aux colonnes de la source de données externe.  
  
 Vous pouvez également cliquer sur le lien **\<Mapping >** en surbrillance dans le volet requête DMX.  
  
 **Ajouter une sortie**  
 Cliquez pour sélectionner les colonnes qui correspondent à la sortie dans la requête de prédiction.  
  
 Vous pouvez également cliquer sur le lien **> de sortie \<Add** en surbrillance dans le volet requête DMX.  
  
 **Colonnes de modèle**  
 Répertorie les colonnes du modèle d'exploration de données sélectionné. Une marque en forme de losange en regard du nom de la colonne indique que celle-ci est une colonne prévisible.  
  
 **Colonnes d'entrée**  
 Répertorie les colonnes issues de la source de données externes ajoutées comme entrées.  
  
## <a name="see-also"></a>Voir aussi  
 [Compléments d’exploration de données SQL Server de requêtes &#40;&#41;](query-sql-server-data-mining-add-ins.md)  
  
  
