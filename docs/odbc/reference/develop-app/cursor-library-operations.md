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
ms.openlocfilehash: ad141939a548aa008ef7109d0adaec5b3a8c6c3d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68002004"
---
# <a name="cursor-library-operations"></a>Opérations de bibliothèque de curseurs
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Si une application fonctionne avec une application ODBC *2.x* pilote effectue des appels à ODBC *3.x* bibliothèque de curseurs, l’application peut être en mesure d’utiliser ODBC *3.x* fonctionnalités qui ne sont pas prise en charge par ODBC *2.x* pilote. Writer de l’application doit être prudent comment ces fonctionnalités sont utilisées, toutefois. Utilisation de ODBC *3.x* bibliothèque de curseurs ne rend pas une application ODBC *2.x* pilote dans une application ODBC *3.x* pilote.
