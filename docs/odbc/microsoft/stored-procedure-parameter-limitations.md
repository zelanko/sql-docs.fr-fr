---
title: Limites de paramètres de procédure stockées ( Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bbd748884575791d5f170e95bc5aa465b61624b7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299199"
---
# <a name="stored-procedure-parameter-limitations"></a>Limitations des paramètres des procédures stockées
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Lors de l’exécution des procédures stockées Oracle qui utilisent 10 paramètres de sortie ou plus, l’appel de procédure stockée échouera, résultant en une violation d’accès ou ActiveX Data Objects (ADO) erreur. Cela peut se produire lors de l’utilisation du pilote Microsoft ODBC pour Oracle avec des versions 8.0.4.0.0 et 8.0.4.0.4 du logiciel client Oracle.  
  
 Pour corriger le problème, le logiciel client Oracle doit être mis à niveau vers la version 8.0.4.2.0 ou plus. Contactez Oracle Corporation pour plus d’informations sur [les correctifs](../../odbc/microsoft/oracle-software-patches.md).  
  
> [!NOTE]  
>  Ce problème ne se produit pas avec la sortie anticipée de la version logicielle client Oracle 8.0.3.0.0.
