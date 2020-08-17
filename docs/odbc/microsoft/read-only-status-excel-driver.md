---
description: État En lecture seule (pilote Excel)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 04a0c5d0cb2c9932d30c0edb900169d8c5e5f82b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340385"
---
# <a name="read-only-status-excel-driver"></a>État En lecture seule (pilote Excel)
Lorsque le pilote Microsoft Excel est utilisé, les tables de source de données sont ouvertes en lecture seule par défaut, et ne peuvent être ouvertes que par un seul utilisateur à la fois. Bien que les tables aient un État en lecture seule, toutefois, les applications peuvent effectuer des insertions et des mises à jour pour les tables Microsoft Excel.  
  
 Quand une application exécute une commande Enregistrer sous sur des données Microsoft Excel par le biais du pilote Microsoft Excel, elle doit créer une nouvelle table et insérer les données à enregistrer dans la nouvelle table. Les insertions entraînent un ajout à la table. Aucune autre opération ne peut être effectuée sur la table tant qu’elle n’est pas fermée, puis rouverte. Une fois la table fermée, aucune insertion suivante ne peut être effectuée, car la table est ensuite une table en lecture seule.  
  
 Il est possible de mettre à jour les valeurs lors de l’utilisation du pilote Microsoft Excel, mais une ligne ne peut pas être supprimée d’une table basée sur une feuille de calcul Microsoft Excel, donc les mises à jour ne sont pas considérées comme officiellement prises en charge par le pilote Microsoft Excel.
