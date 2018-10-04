---
title: Enregistrer les métadonnées (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9a76083e-4902-449e-b125-7e9259fc37f7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d12ff5f349d5b7328af7e47dbfc7724420d6fb15
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47674977"
---
# <a name="save-metadata-db2tosql"></a>Enregistrer les métadonnées (DB2ToSQL)
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
  
