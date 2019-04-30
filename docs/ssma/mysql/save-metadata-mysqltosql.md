---
title: Enregistrer les métadonnées (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9bc6273f-e8b1-430b-81a5-14330a783562
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: f641b27357e75db0fb0f6ef71ff701d4f04b45a5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63154573"
---
# <a name="save-metadata--mysqltosql"></a>Enregistrer les métadonnées (MySQLToSQL)
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
  
