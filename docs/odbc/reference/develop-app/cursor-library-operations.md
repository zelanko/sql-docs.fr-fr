---
title: Bibliothèque de curseurs | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], backward compatibility
- compatibility [ODBC], cursor library
- upgrading applications [ODBC], cursor library
- application upgrades [ODBC], cursor library
- backward compatibility [ODBC], cursor library
- cursor library [ODBC], backward compatibility
ms.assetid: 04d514b1-dc4d-4b84-bf35-60f4657ef1f6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 748d917ad060609d40e40a24e5669cff37188691
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792660"
---
# <a name="cursor-library-operations"></a>Opérations de bibliothèque de curseurs
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Si une application fonctionne avec une application ODBC *2.x* pilote effectue des appels à ODBC *3.x* bibliothèque de curseurs, l’application peut être en mesure d’utiliser ODBC *3.x* fonctionnalités qui ne sont pas prise en charge par ODBC *2.x* pilote. Writer de l’application doit être prudent comment ces fonctionnalités sont utilisées, toutefois. Utilisation de ODBC *3.x* bibliothèque de curseurs ne rend pas une application ODBC *2.x* pilote dans une application ODBC *3.x* pilote.
