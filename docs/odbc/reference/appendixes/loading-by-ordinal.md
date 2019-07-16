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
ms.openlocfilehash: fdc7728fe06df708efd973423f5c8c05333ce189
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041603"
---
# <a name="loading-by-ordinal"></a>Chargement par ordinal
Dans ODBC *2.x*, le chargement par ordinal pourrait être effectué pour améliorer les performances du processus de connexion. Une application ODBC *2.x* pilote exporte une fonction factice de l’ordinal 199 ; lorsque le Gestionnaire de pilote détecte que celui-ci, il résout les adresses des fonctions ODBC par ordinal, et non par nom. Cette fonctionnalité est toujours pris en charge pour ODBC *2.x* pilotes mais n’est ne pas pris en charge pour ODBC *3.x* pilotes.
