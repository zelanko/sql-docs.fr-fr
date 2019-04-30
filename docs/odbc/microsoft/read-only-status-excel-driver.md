---
title: État en lecture seule (pilote Excel) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- read-only status for Excel driver [ODBC]
- Excel driver [ODBC], read-only status
ms.assetid: ef5d773b-4f8f-4005-b985-84b53d8e9f9b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 17425e76814a8397b9d2e6167248f35e52ac6cfa
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63316736"
---
# <a name="read-only-status-excel-driver"></a>État En lecture seule (pilote Excel)
Lorsque le pilote Microsoft Excel est utilisé, les tables de source de données sont ouverts en lecture seule par défaut et peuvent être ouvert par un seul utilisateur à la fois. Même si les tables ont un état en lecture seule, toutefois, applications peuvent effectuer les insertions et mises à jour pour les tables de Microsoft Excel.  
  
 Lorsqu’une application exécute une commande Enregistrer en tant que données de Microsoft Excel via le pilote Microsoft Excel, l’application doit créer une nouvelle table et insérer les données doit être enregistré dans la nouvelle table. Insertions entraînent un ajout à la table. Aucune autre opération ne peut être effectuée sur la table jusqu'à ce qu’elle est fermée et rouverte. Une fois que la table est fermée, aucune insertion suivante ne peut être effectuée, car la table est ensuite une table en lecture seule.  
  
 Il est possible de mettre à jour les valeurs lorsque vous utilisez le pilote Microsoft Excel, mais une ligne ne peut pas être supprimée à partir d’une table basée sur une feuille de calcul Microsoft Excel, les mises à jour sont considérées comme pas officiellement pris en charge par le pilote Microsoft Excel.
