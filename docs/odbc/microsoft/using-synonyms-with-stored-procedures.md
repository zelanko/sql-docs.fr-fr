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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6e798a9c7fa3365082a2e6dab562596d56649ec4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088024"
---
# <a name="using-synonyms-with-stored-procedures"></a>Utilisation de synonymes avec des procédures stockées
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Le pilote Microsoft ODBC pour Oracle versions 2,0 et 2,5 ne prend pas en charge les synonymes lors de l’appel de procédures stockées Oracle. Les synonymes fonctionnent comme prévu lorsqu’ils sont utilisés avec d’autres objets de base de données Oracle, tels que des tables.
