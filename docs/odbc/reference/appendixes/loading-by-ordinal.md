---
title: Le chargement par Ordinal | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 702e1fe58080cc370ab9a858c985a7744df85050
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181334"
---
# <a name="loading-by-ordinal"></a>Chargement par ordinal
Dans ODBC 2. *x*, le chargement par ordinal pourrait être effectué pour améliorer les performances du processus de connexion. Une application ODBC 2. *x* pilote exporte une fonction factice de l’ordinal 199 ; lorsque le Gestionnaire de pilote détecte que celui-ci, il résout les adresses des fonctions ODBC par ordinal, et non par nom. Cette fonctionnalité est toujours pris en charge pour ODBC 2. *x* pilotes mais n’est ne pas pris en charge pour ODBC 3 *.x* pilotes.
