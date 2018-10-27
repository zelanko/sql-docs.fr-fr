---
title: Paramètres (Conversion) (AccessToSQL) du projet | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- conversion, options described
- Project Settings dialog box, Conversion
ms.assetid: bcebc635-c638-4ddb-924c-b9ccfef86388
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 6122efd4340fb223e42ffa77b5851380be23b0c0
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50099370"
---
# <a name="project-settings-conversion-accesstosql"></a>Paramètres du projet (Conversion) (AccessToSQL)
Les paramètres de projet de Conversion vous permettent de configurer le mode de conversion des objets à partir d’objets de base de données Access à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou objets de base de données SQL Azure.  
  
Le volet de la Conversion est disponible dans le **paramètres du projet** et **par défaut des paramètres de projet** boîtes de dialogue.  
  
-   Utilisez le **paramètres du projet** boîte de dialogue pour définir les options de configuration pour le projet actuel. Pour accéder aux paramètres de conversion, sur le **outils** menu, sélectionnez **paramètres du projet**, cliquez sur **général** en bas du volet gauche, puis sélectionnez  **Conversion**.  
  
-   Utilisez le **par défaut des paramètres de projet** boîte de dialogue pour définir les options de configuration pour tous les projets. Pour accéder aux paramètres de conversion, sur le **outils** menu, sélectionnez **par défaut des paramètres de projet**, sélectionnez le type de projet de migration pour lequel les paramètres sont requis pour être affiché / a été remplacée par  **Version cible de migration** liste déroulante, cliquez sur **général** en bas du volet gauche, puis sélectionnez **Conversion**.  
  
## <a name="options"></a>Options  
**Ajouter une clé primaire**  
Crée une nouvelle clé primaire dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou une table SQL Azure si une table Access n’a aucune clé primaire ou un index unique.  
  
-   **Par défaut en Mode**: False  
  
-   **Mode optimiste**: False  
  
-   **Mode plein**: True  
  
Lorsque connecté à SQL Azure, il est par défaut la valeur True. **Ajouter des colonnes timestamp**  
Spécifie si SSMA doit créer une valeur d’horodatage si nécessaire.  
  
-   **Par défaut en Mode**: SSMA permettent de décider  
  
-   **Mode optimiste**: jamais  
  
-   **Mode plein**: SSMA permettent de décider  
  
**Inclure un rapport d’évaluation de données avec la conversion des rapports d’évaluation**  
Inclut une évaluation des données dans le rapport d’évaluation.  
  
-   **Par défaut en Mode**: True  
  
-   **Mode optimiste**: False  
  
-   **Mode plein**: True  
  
**Type de message lorsqu’une clé primaire comprend des colonnes de type nullable**  
Spécifie le type de message (avertissement, erreur ou rien) indiquant SSMA dans le volet de sortie lorsqu’il détecte des clés primaires avec les colonnes de type nullable.  
  
-   **Par défaut en Mode**: avertissement  
  
-   **Mode optimiste**: aucun message  
  
-   **Mode plein**: erreur  
  
**Type de message lorsque les colonnes clés étrangères sont de tailles différentes**  
Spécifie le type de message (avertissement, erreur ou rien) indiquant SSMA dans le volet de sortie lorsqu’il détecte une clé étrangère incorrecte de texte.  
  
-   **Par défaut en Mode**: avertissement  
  
-   **Mode optimiste**: aucun message  
  
-   **Mode plein**: erreur  
  
**Type de message lorsque les colonnes Mémo sont indexées.**  
Spécifie le type de message (avertissement, erreur ou rien) indiquant SSMA dans le volet de sortie lorsqu’il détecte un index qui contient un **mémo** colonne.  
  
-   **Par défaut en Mode**: avertissement  
  
-   **Mode optimiste**: aucun message  
  
-   **Mode plein**: erreur  
  
**Avertir en cas d’une requête complexe utilise un caractère générique (\&#42 ;)**  
Affiche un avertissement dans le volet de sortie et liste d’erreurs lorsqu’un nom de colonne dans une instruction SELECT est un caractère générique (*).  
  
-   **Par défaut en Mode**: True  
  
-   **Mode optimiste**: False  
  
-   **Mode plein**: True  
  
**Avertir lorsque le nom d’identificateur est modifié.**  
Affiche un message dans le rapport d’évaluation et dans le volet de sortie lorsqu’un nom d’identificateur objet est modifié par SSMA.  
  
-   **Par défaut en Mode**: True  
  
-   **Mode optimiste**: False  
  
-   **Mode plein**: True  
  
**Avertir en cas d’identificateur sera être mis entre guillemets.**  
Affiche un message dans le rapport d’évaluation et dans le volet de sortie lorsque le nom d’identificateur d’objet sera être mis entre guillemets par SSMA. Les identificateurs sont nécessaire lorsque le nom est un mot clé ou contient des caractères spéciaux.  
  
-   **Par défaut en Mode**: True  
  
-   **Mode optimiste**: False  
  
-   **Mode plein**: True  
  
## <a name="see-also"></a>Voir aussi  
[Reference(Access) d’Interface utilisateur](http://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
