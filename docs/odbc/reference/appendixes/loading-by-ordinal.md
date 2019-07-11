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
ms.openlocfilehash: ccecc541143e971d82a225e24e1c8caf6a03c32c
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793190"
---
# <a name="loading-by-ordinal"></a>Chargement par ordinal
Dans ODBC *2.x*, le chargement par ordinal pourrait être effectué pour améliorer les performances du processus de connexion. Une application ODBC *2.x* pilote exporte une fonction factice de l’ordinal 199 ; lorsque le Gestionnaire de pilote détecte que celui-ci, il résout les adresses des fonctions ODBC par ordinal, et non par nom. Cette fonctionnalité est toujours pris en charge pour ODBC *2.x* pilotes mais n’est ne pas pris en charge pour ODBC *3.x* pilotes.
