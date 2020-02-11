---
title: Chargement par ordinal | Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041603"
---
# <a name="loading-by-ordinal"></a>Chargement par ordinal
Dans ODBC *2. x*, le chargement par ordinal peut être effectué pour améliorer les performances du processus de connexion. Un pilote ODBC *2. x* exporte une fonction factice avec l’ordinal 199 ; Quand le gestionnaire de pilotes le détecte, il résout les adresses des fonctions ODBC par ordinal, et non par nom. Cette fonctionnalité est toujours prise en charge pour les pilotes ODBC *2. x* , mais n’est pas prise en charge pour les pilotes ODBC *3. x* .
