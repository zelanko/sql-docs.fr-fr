---
title: Stockées des Limitations de paramètre de procédure | Microsoft Docs
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
ms.assetid: 8b804bcf-4cce-4e6f-aa45-00bab9ef9921
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 36f1c5a18eb9f0b1939a2c3602f1ebe7695741f7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67948828"
---
# <a name="stored-procedure-parameter-limitations"></a>Limitations des paramètres des procédures stockées
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Lorsque Oracle en cours d’exécution des procédures stockées qui utilisent 10 ou plusieurs paramètres de sortie, l’appel de procédure stockée échoue, ce qui entraîne une erreur de Violation d’accès ou ActiveX Data Objects (ADO). Cela peut se produire lorsque vous utilisez le pilote Microsoft ODBC pour Oracle avec les versions 8.0.4.0.0 et 8.0.4.0.4 du logiciel client Oracle.  
  
 Pour corriger le problème, le logiciel client Oracle doit être mis à niveau vers la version 8.0.4.2.0 ou une version ultérieure. Contactez Oracle Corporation pour plus d’informations sur la [correctifs](../../odbc/microsoft/oracle-software-patches.md).  
  
> [!NOTE]  
>  Ce problème ne se produit pas avec la première version du logiciel client Oracle version 8.0.3.0.0.
