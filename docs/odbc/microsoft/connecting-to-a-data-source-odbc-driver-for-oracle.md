---
title: "Connexion à une Source de données (le pilote ODBC pour Oracle) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connecting to data source [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], connecting to data sources
ms.assetid: f724a9c5-342a-4f4e-a030-ec34f7378eaf
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 054c274bc65c0f4ecf149607216f62e9e15df225
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-to-a-data-source-odbc-driver-for-oracle"></a>Connexion à une Source de données (le pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Une application ODBC peut transmettre des informations de connexion de plusieurs façons. Par exemple, l’application peut avoir le pilote d’inviter l’utilisateur pour les informations de connexion. Ou l’application peut attendre une chaîne de connexion qui spécifie la connexion de source de données. Comment vous connectez à une source de données dépend de la méthode de connexion utilisée par votre application ODBC.  
  
 La boîte de dialogue Source de données est un moyen classique pour se connecter à une source de données. Si votre application ODBC est configurée pour utiliser une boîte de dialogue, cette boîte de dialogue s’affiche et vous demande les informations de connexion de source de données approprié.  
  
 Vous pouvez également vous connecter à une source de données à l’aide du [chaîne de connexion](../../odbc/microsoft/connection-string-format-and-attributes.md).  
  
### <a name="to-connect-to-a-data-source-using-a-dialog-box"></a>Pour vous connecter à une source de données à l’aide d’une boîte de dialogue  
  
1.  La boîte de dialogue Source de données s’affiche, sélectionnez une source de données Oracle, puis cliquez sur OK. La boîte de dialogue de connexion s’affiche.  
  
2.  Renseignez les informations appropriées pour la boîte de dialogue se connecter, puis cliquez sur OK.  
  
 Une fois la connexion le cas échéant, votre application peut utiliser le pilote ODBC pour Oracle pour accéder aux informations de la source de données contient.

