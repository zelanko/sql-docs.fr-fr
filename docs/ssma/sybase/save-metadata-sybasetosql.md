---
title: Enregistrer les métadonnées (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: b2517735-dd19-449f-8cee-08e68ca89d3a
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 8321c6e8a63eb4baabde580a911dccec6ab9ff3e
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87930341"
---
# <a name="save-metadata--sybasetosql"></a>Enregistrer les métadonnées (SybaseToSQL)
La boîte de dialogue **enregistrer les métadonnées** vous invite à charger les métadonnées dans votre projet SSMA avant de l’enregistrer. Cela vous permet d’avoir un fichier projet complet que vous pouvez utiliser en mode hors connexion et l’envoyer à d’autres personnes, telles que le personnel du support technique.  
  
Pour accéder à la boîte de dialogue **enregistrer les métadonnées** , enregistrez le projet. Si des métadonnées sont manquantes, SSMA affiche la boîte de dialogue **enregistrer les métadonnées** .  
  
## <a name="options"></a>Options  
**Nom**  
Nom de chaque base de données dans le projet.  
  
**État**  
Indique si les métadonnées sont chargées dans le projet SSMA ou si des métadonnées sont manquantes.  
  
SSMA charge les métadonnées dans le projet, si nécessaire. Les métadonnées sont chargées automatiquement lorsque vous parcourez les métadonnées et convertissez les schémas.  
  
**Sélectionner tout**  
Sélectionne toutes les bases de données listées.  
  
**Clear**  
Désactive la case à cocher de toutes les bases de données avec des métadonnées manquantes. Vous ne pouvez pas désactiver la case à cocher si des métadonnées ont été chargées.  
  
**Save**  
Enregistre le projet, en chargeant les métadonnées des bases de données sélectionnées qui ont des métadonnées manquantes.  
  
**Annuler**  
Annule l’opération d’enregistrement. Les métadonnées manquantes ne sont pas chargées dans le projet.  
  
