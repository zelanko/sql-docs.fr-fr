---
title: Connexion à une source de données (pilote ODBC pour Oracle) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to data source [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], connecting to data sources
ms.assetid: f724a9c5-342a-4f4e-a030-ec34f7378eaf
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6ef567c9e3c7b63e7f5044de699750de856f3e52
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81281299"
---
# <a name="connecting-to-a-data-source-odbc-driver-for-oracle"></a>Connexion à une source de données (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Une application ODBC peut transmettre des informations de connexion de plusieurs façons. Par exemple, l’application peut demander au pilote de toujours inviter l’utilisateur à entrer les informations de connexion. Ou l’application peut attendre une chaîne de connexion qui spécifie la connexion à la source de données. La façon dont vous vous connectez à une source de données dépend de la méthode de connexion utilisée par votre application ODBC.  
  
 Une façon courante de se connecter à une source de données consiste à utiliser la boîte de dialogue source de données. Si votre application ODBC est configurée pour utiliser une boîte de dialogue, cette boîte de dialogue s’affiche et vous invite à entrer les informations de connexion à la source de données appropriées.  
  
 Vous pouvez également vous connecter à une source de données à l’aide de la [chaîne de connexion](../../odbc/microsoft/connection-string-format-and-attributes.md).  
  
### <a name="to-connect-to-a-data-source-using-a-dialog-box"></a>Pour se connecter à une source de données à l’aide d’une boîte de dialogue  
  
1.  Lorsque la boîte de dialogue source de données s’affiche, sélectionnez une source de données Oracle, puis cliquez sur OK. La boîte de dialogue Connecter s'affiche.  
  
2.  Renseignez les informations appropriées pour la boîte de dialogue de connexion, puis cliquez sur OK.  
  
 Une fois les informations de connexion vérifiées, votre application peut utiliser le pilote ODBC pour Oracle pour accéder aux informations contenues dans la source de données.
