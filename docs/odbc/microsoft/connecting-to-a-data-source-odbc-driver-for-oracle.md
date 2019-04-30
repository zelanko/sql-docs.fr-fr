---
title: Connexion à une Source de données (pilote ODBC pour Oracle) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: adee8d8dd8d6db0d79b37ff853c41e7604fe21de
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63302132"
---
# <a name="connecting-to-a-data-source-odbc-driver-for-oracle"></a>Connexion à une source de données (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Une application ODBC peut transmettre des informations de connexion de plusieurs façons. Par exemple, l’application peut avoir le pilote d’inviter l’utilisateur pour les informations de connexion. Ou l’application peut attendre une chaîne de connexion qui spécifie la connexion de source de données. Comment vous connectez à une source de données dépend de la méthode de connexion utilisée par votre application ODBC.  
  
 Une méthode courante pour se connecter à une source de données est via la boîte de dialogue Source de données. Si votre application ODBC est configurée pour utiliser une boîte de dialogue, cette boîte de dialogue s’affiche et vous invite à entrer les informations de connexion de source de données approprié.  
  
 Vous pouvez également vous connecter à une source de données à l’aide de la [chaîne de connexion](../../odbc/microsoft/connection-string-format-and-attributes.md).  
  
### <a name="to-connect-to-a-data-source-using-a-dialog-box"></a>Pour vous connecter à une source de données à l’aide d’une boîte de dialogue  
  
1.  Lorsque la boîte de dialogue Source de données s’affiche, sélectionnez une source de données Oracle, puis sur OK. La boîte de dialogue de connexion s’affiche.  
  
2.  Renseignez les informations appropriées pour la boîte de dialogue se connecter, puis cliquez sur OK.  
  
 Une fois la connexion des informations sont vérifiées, votre application peut utiliser le pilote ODBC pour Oracle pour accéder aux informations qui contient la source de données.
