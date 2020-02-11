---
title: Utilisation des services de composants Microsoft | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 91d6dcf0ca7f87d6ed510d582f7a7ba0f80e8c74
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088151"
---
# <a name="using-microsoft-component-services"></a>Utilisation des services de composants Microsoft
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Vous pouvez activer une base de données Oracle pour fonctionner avec les services de composants transactionnels (ou MTS, si vous utilisez Windows NT) sur Microsoft Windows NT/Windows 2000 et Microsoft Windows 95/98. Pour permettre à une base de données Oracle de fonctionner avec les services de composants qui prennent en charge les transactions, les administrateurs système doivent créer une vue nommée V $ XATRANS $. Pour créer ce script, vous devez exécuter un script fourni par Oracle. Pour plus d’informations, consultez l’aide des services de composants ou votre documentation Oracle.
