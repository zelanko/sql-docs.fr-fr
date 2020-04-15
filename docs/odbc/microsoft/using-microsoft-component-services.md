---
title: Utilisation des services de composants Microsoft (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], component services
- component services [ODBC]
ms.assetid: 06450562-d8f3-4987-b7bd-4a70223ff937
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fb5763058fa198cbad7464434e31942ef8d6cd7d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307580"
---
# <a name="using-microsoft-component-services"></a>Utilisation des services de composants Microsoft
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Vous pouvez activer une base de données Oracle pour travailler avec les services de composants transactionnels (ou MTS, si vous utilisez Windows NT) sur Microsoft Windows NT/Windows 2000 et Microsoft Windows 95/98. Pour permettre à une base de données Oracle de travailler avec component Services qui prennent en charge les transactions, les administrateurs du système devraient créer une vue nommée V$XATRANS$. Pour créer ce script, vous devez exécuter un script fourni par Oracle. Pour plus d’informations, consultez l’aide aux composants ou votre documentation Oracle.
