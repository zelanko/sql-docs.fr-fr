---
title: Utilisation de synonymes avec des procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 8620b039-a086-4534-8710-cc8b1787dc80
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6d3758aeb954427f333c5a22298d6675c04acdb5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81292759"
---
# <a name="using-synonyms-with-stored-procedures"></a>Utilisation de synonymes avec des procédures stockées
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Le pilote Microsoft ODBC pour Oracle versions 2,0 et 2,5 ne prend pas en charge les synonymes lors de l’appel de procédures stockées Oracle. Les synonymes fonctionnent comme prévu lorsqu’ils sont utilisés avec d’autres objets de base de données Oracle, tels que des tables.
