---
title: Chargement par Ordinal Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], loading by ordinal
- compatibility [ODBC], loading by ordinal
- loading by ordinal [ODBC]
ms.assetid: 337d90ab-68eb-4940-a2f3-f7d5693ee766
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 64bff8dcdd3802f75dc402c9ada60f82580aca5c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288719"
---
# <a name="loading-by-ordinal"></a>Chargement par ordinal
Dans ODBC *2.x*, le chargement par ordinal pourrait être effectué pour améliorer les performances du processus de connexion. Un conducteur ODBC *2.x* exporte une fonction factice avec l’ordinaire 199; lorsque le gestionnaire de conducteur le détecte, il résout les adresses des fonctions ODBC par ordinaire, et non par son nom. Cette fonctionnalité est toujours prise en charge pour les pilotes ODBC *2.x,* mais n’est pas pris en charge pour les pilotes ODBC *3.x.*
