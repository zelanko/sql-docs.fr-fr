---
title: Enregistrer les métadonnées (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: b2517735-dd19-449f-8cee-08e68ca89d3a
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 8bfe338c128ce301e98346d17ce00b973912ffd4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62667516"
---
# <a name="save-metadata--sybasetosql"></a>Enregistrer les métadonnées (SybaseToSQL)
Le **enregistrer les métadonnées** boîte de dialogue vous invite à charger les métadonnées dans votre projet SSMA avant de l’enregistrer. Vous pouvez ainsi vous disposez d’un fichier de projet complet que vous pouvez utiliser hors connexion et l’envoyer à d’autres personnes, tels que du personnel de support technique.  
  
Pour accéder à la **enregistrer les métadonnées** boîte de dialogue, enregistrez le projet. Si toutes les métadonnées sont manquante, SSMA affichera le **enregistrer les métadonnées** boîte de dialogue.  
  
## <a name="options"></a>Options  
**Nom**  
Le nom de chaque base de données dans le projet.  
  
**État**  
Indique si les métadonnées sont chargées dans le projet SSMA, ou si les métadonnées sont manquantes.  
  
SSMA charge les métadonnées dans le projet en fonction des besoins. Métadonnées sont chargées automatiquement lorsque vous parcourez les métadonnées et convertissez des schémas.  
  
**Tout sélectionner**  
Sélectionne les bases de données tout répertoriées.  
  
**Désactiver**  
Efface la case à cocher pour toutes les bases de données avec les métadonnées manquantes. Impossible d’effacer la case à cocher si une entrée de métadonnées a été chargée.  
  
**Enregistrer**  
Enregistre le projet, le chargement des métadonnées pour les bases de données sélectionnées qui ne disposent pas de métadonnées.  
  
**Annuler**  
Annule l’enregistrement opération. Les métadonnées manquantes ne sont pas chargée dans le projet.  
  
