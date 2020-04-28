---
title: Limitations des paramètres des procédures stockées | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299199"
---
# <a name="stored-procedure-parameter-limitations"></a>Limitations des paramètres des procédures stockées
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Lorsque vous exécutez des procédures stockées Oracle qui utilisent 10 paramètres de sortie ou plus, l’appel de procédure stockée échoue, provoquant une erreur de violation d’accès ou d’ActiveX Data Objects (ADO). Cela peut se produire lors de l’utilisation du pilote Microsoft ODBC pour Oracle avec les versions 8.0.4.0.0 et 8.0.4.0.4 du logiciel client Oracle.  
  
 Pour résoudre le problème, le logiciel client Oracle doit être mis à niveau vers la version 8.0.4.2.0 ou ultérieure. Pour plus d’informations sur les [correctifs](../../odbc/microsoft/oracle-software-patches.md), contactez Oracle Corporation.  
  
> [!NOTE]  
>  Ce problème ne se produit pas avec la version préliminaire de la version 8.0.3.0.0 du logiciel client Oracle.
