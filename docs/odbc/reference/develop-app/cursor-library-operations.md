---
title: Opérations de la bibliothèque de curseurs | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a2297e72aacad7ea91b7af934a47bebbc61f0686
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301616"
---
# <a name="cursor-library-operations"></a>Opérations de bibliothèque de curseurs
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande l’utilisation de la fonctionnalité de curseur du pilote.  
  
 Si une application qui utilise un pilote ODBC *2. x* appelle la bibliothèque de curseurs ODBC *3.* x, l’application peut être en mesure d’utiliser les fonctionnalités ODBC *3. x* qui ne sont pas prises en charge par le pilote ODBC *2. x* . Toutefois, un enregistreur d’applications doit faire attention à la façon dont ces fonctionnalités sont utilisées. L’utilisation de la bibliothèque de curseurs ODBC *3. x* ne fait pas d’un pilote ODBC *2. x* dans un pilote ODBC *3. x* .
