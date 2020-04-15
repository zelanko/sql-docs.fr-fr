---
title: Statut De lecture seulement (Pilote Excel) Microsoft Docs
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
ms.openlocfilehash: eb585d4712b6cac5e09b65ee8e13604763cd0164
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304020"
---
# <a name="read-only-status-excel-driver"></a>État En lecture seule (pilote Excel)
Lorsque le pilote Microsoft Excel est utilisé, les tables de source de données sont ouvertes uniquement par défaut et peuvent être ouvertes par un seul utilisateur à la fois. Même si les tables ont un statut de lecture seulement, cependant, les applications peuvent effectuer des insertions et des mises à jour pour les tables Microsoft Excel.  
  
 Lorsqu’une application effectue une commande Save As sur les données Microsoft Excel via le pilote Microsoft Excel, l’application doit créer une nouvelle table et insérer les données à enregistrer dans la nouvelle table. Les inserts donnent lieu à un appendice à la table. Aucune autre opération ne peut être effectuée sur la table tant qu’elle n’est pas fermée et rouverte. Une fois la table fermée, aucun insert ultérieur ne peut être exécuté parce que la table est alors une table de lecture seulement.  
  
 Il est possible de mettre à jour les valeurs lors de l’utilisation du pilote Microsoft Excel, mais une ligne ne peut pas être supprimée d’une table basée sur une feuille de calcul Microsoft Excel, de sorte que les mises à jour ne sont pas considérées officiellement pris en charge par le pilote Microsoft Excel.
