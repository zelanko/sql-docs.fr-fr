---
title: Commande INDEX (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- index command [ODBC]
ms.assetid: 694e8cf5-2f69-4001-9c1e-b735a4da3aff
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bcb30a49cb9f11ddd4c61621116aa4bd8ddcf186
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300029"
---
# <a name="index-command"></a>INDEX, commande
Crée un fichier d’index pour afficher et accéder aux enregistrements de table dans un ordre logique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
INDEX ON eExpression TO IDXFileName | TAG TagName [OF CDXFileName]  
   [FOR lExpression]  
   [COMPACT]  
   [ASCENDING | DESCENDING]  
   [UNIQUE | CANDIDATE]  
   [ADDITIVE]  
```  
  
## <a name="arguments"></a>Arguments  
 *eExpression*  
 Spécifie une expression d’index qui peut inclure le nom d’un champ ou des champs à partir du tableau actuel. Une clé d’index basée sur l’expression de l’index est créée dans le fichier d’index pour chaque enregistrement du tableau. Visual FoxPro utilise ces touches pour afficher et accéder aux enregistrements dans la table.  
  
> [!NOTE]  
>  Bien qu’il ne soit pas recommandé, *l’eExpression* peut également être une variable de mémoire, un élément de tableau, ou une expression de champ ou de champ d’une table dans une autre zone de travail. Les champs de notes ne peuvent pas être utilisés seuls dans les expressions de fichiers index; ils doivent être combinés avec d’autres expressions de caractère. Si vous accédez à un index qui contient une variable ou un champ qui n’existe plus ou ne peut pas être localisé, Visual FoxPro génère un message d’erreur.  
  
 Si vous essayez de construire un index avec une clé qui varie en longueur, la clé sera rembourrée avec des espaces. Les touches d’index à longueur variable ne sont pas prises en charge dans Visual FoxPro.  
  
 Il est possible de créer une clé d’index avec une longueur nulle. Par exemple, une clé d’index de longueur zéro est créée lorsque l’expression de l’index est une sous-corde d’un champ de mémo vide. Une clé d’index de longueur zéro génère un message d’erreur. Lorsque Visual FoxPro crée un index, il évalue les champs dans le premier enregistrement dans le tableau. Si un champ est vide, il pourrait être nécessaire d’entrer des données temporaires sur le terrain dans le premier enregistrement pour empêcher une clé d’index de 0 longueur.  
  
 À *IDXFileName*  
 Crée un fichier index .idx. Le fichier index est donné l’extension par défaut .idx.  
  
 TAG *TagName*[OF *CDXFileName*]  
 Crée un fichier d’index composé. Un fichier d’index composé est un fichier d’index unique qui se compose d’un certain nombre d’étiquettes distinctes (entrées d’index). Chaque balise est identifiée par son nom unique. Les noms d’étiquette doivent commencer par une lettre ou un soulignement et peuvent se composer de n’importe quelle combinaison de jusqu’à 10 lettres, chiffres, ou souligne. Le nombre d’étiquettes dans un fichier d’index composé n’est limité que par la mémoire disponible et l’espace disque.  
  
 Les fichiers d’index composés à entrées multiples sont toujours compacts. Il n’est pas nécessaire d’inclure COMPACT lors de la création d’un fichier d’index composé. Les noms des fichiers index composés sont donnés une extension .cdx.  
  
 Deux types de fichiers d’index composés peuvent être créés : structurel et non structurel.  
  
 **Fichiers d’indices composés structurels** Vous pouvez créer un fichier d’index composé structurel avec TAG *TagName* en excluant la clause *CDXFileName* optionnelle. Un fichier d’index composé structurel a toujours le même nom de base que la table et est automatiquement ouvert lorsque la table est ouverte.  
  
 **Fichiers d’index composés nontructuraux** Vous pouvez créer un fichier d’index composé nontructural en incluant OF *CDXFileName* d’après TAG *TagName*. Contrairement à un fichier d’index composé structurel, un fichier d’index composé non structurel doit être explicitement ouvert avec la clause INDEX dans USE.  
  
 Si un fichier d’index composé a déjà été créé et ouvert, l’émission d’INDEX avec TAG *TagName* ajoute une étiquette au fichier d’index composé.  
  
 POUR *lExpression*  
 Spécifie une condition par laquelle seuls les enregistrements qui satisfont *l’expression du filtre lExpression* sont disponibles pour l’affichage et l’accès; les clés d’index sont créées dans le fichier d’index pour seulement les enregistrements correspondant à l’expression du filtre.  
  
 La technologie Visuelle FoxPro Rushmore optimise un INDEX ... POUR la commande *d’expression* si *lExpression* est une expression optimisée. Pour obtenir de meilleures performances, utilisez une expression optimisée dans la clause FOR.  
  
 Compact  
 Crée un fichier .idx compact.  
  
 Ascendant  
 Spécifie une commande ascendante pour le fichier .cdx. Par défaut, les balises .cdx sont créées dans l’ordre ascendant. (Vous pouvez inclure ASCENDING comme un rappel de l’ordre du fichier d’index.) Un tableau peut être indexé dans l’ordre inverse en incluant DESCENDING.  
  
 Descendant  
 Spécifie une commande descendante pour le fichier .cdx. Vous ne pouvez pas inclure DESCENDING lors de la création de fichiers d’index .idx.  
  
 UNIQUE  
 Précise que seul le premier enregistrement rencontré avec une valeur clé d’index particulière est inclus dans un fichier .idx ou une balise .cdx. UNIQUE peut être utilisé pour empêcher l’affichage ou l’accès à des enregistrements en double. Tous les enregistrements ajoutés avec des clés d’index en double sont exclus du fichier indiciel. L’utilisation de l’option UNIQUE d’INDEX est identique à l’exécution de SET UNIQUE ON avant d’émettre INDEX ou REINDEX.  
  
 Lorsqu’un index ou une étiquette d’index UNIQUE est actif et qu’un enregistrement en double est modifié d’une manière qui modifie sa clé d’index, l’indice ou l’étiquette d’index est mis à jour. Toutefois, le prochain enregistrement en double avec la clé d’index d’origine ne peut pas être consulté ou affiché jusqu’à ce que vous réindexez le fichier à l’aide de REINDEX.  
  
 Candidat  
 Crée une étiquette d’index structurel candidat. Le mot clé CANDIDATE ne peut être inclus que lors de la création d’une étiquette d’index structurel; autrement, Visual FoxPro génère un message d’erreur.  
  
 Une étiquette d’index candidat empêche les valeurs en double dans le domaine ou la combinaison de champs spécifiés dans l’expression de l’index *eExpression*. Le *terme candidat* fait référence au type d’indice; parce que les indices candidats empêchent les valeurs en double, ils se qualifient comme un «candidat» pour être un indice primaire.  
  
 Visual FoxPro génère une erreur si vous créez une balise d’index de candidat pour un champ ou une combinaison de champs qui contient déjà des valeurs en double.  
  
 Additif  
 Garde ouvert tous les fichiers index précédemment ouverts. Si vous ometez la clause ADDITIVE lorsque vous créez un fichier indiciel ou des fichiers pour une table avec INDEX, tous les fichiers indiciels précédemment ouverts (à l’exception de l’indice composé structurel) sont fermés.  
  
## <a name="remarks"></a>Notes  
 Les enregistrements d’un tableau dont le fichier d’index est affiché et consulté dans l’ordre spécifié par l’expression de l’index. L’ordre physique des enregistrements dans le tableau n’est pas modifié par un fichier d’index.  
  
## <a name="index-types"></a>Types d’indices  
 Visual FoxPro vous permet de créer deux types de fichiers index :  
  
-   Fichiers d’index composés .cdx contenant plusieurs entrées d’index appelées balises  
  
-   fichiers d’index .idx contenant une entrée d’index  
  
 Vous pouvez également créer un fichier d’index composé structurel, qui est automatiquement ouvert avec la table.  
  
> [!NOTE]  
>  Étant donné que les fichiers d’index composés structurels sont automatiquement ouverts lorsque la table est ouverte, ils sont le type d’index préféré.  
  
 Inclure COMPACT pour créer des fichiers index .idx compacts. Les fichiers index composés sont toujours compacts.  
  
## <a name="index-order-and-updating"></a>Ordre et mise à jour de l’indice  
 Un seul fichier d’index (le fichier d’index principal) ou tag (l’étiquette principale) contrôle l’ordre dans lequel la table est affichée ou accessible. Certaines commandes (SEEK, par exemple) utilisent le fichier ou l’étiquette de l’index principal pour rechercher des enregistrements. Cependant, tous les fichiers index .idx ouverts et .cdx sont mis à jour au fur et à mesure que des modifications sont apportées à la table.  
  
## <a name="user-defined-functions"></a>Fonctions définies par l'utilisateur  
 Bien qu’une expression d’index puisse contenir une fonction définie par l’utilisateur, vous ne devez pas utiliser des fonctions définies par l’utilisateur dans une expression index. Les fonctions définies par l’utilisateur dans une expression indexatrice augmentent le temps qu’il faut pour créer ou mettre à jour l’index. En outre, les mises à jour indiciels peuvent ne pas se produire lorsqu’une fonction définie par l’utilisateur est utilisée pour une expression indicatrice.  
  
 Si vous utilisez une fonction définie par l’utilisateur dans une expression index, Visual FoxPro doit être en mesure de localiser la fonction définie par l’utilisateur. Lorsque Visual FoxPro crée un index, l’expression de l’index est enregistrée dans le fichier indiciel, mais seule une référence à la fonction définie par l’utilisateur est incluse dans l’expression de l’index.  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TABLE - Commandement SQL](../../odbc/microsoft/alter-table-sql-command.md)   
 [Commande TAG DELETE](../../odbc/microsoft/delete-tag-command.md)   
 [Set COLLATE Commande](../../odbc/microsoft/set-collate-command.md)   
 [SET UNIQUE, commande](../../odbc/microsoft/set-unique-command.md)
