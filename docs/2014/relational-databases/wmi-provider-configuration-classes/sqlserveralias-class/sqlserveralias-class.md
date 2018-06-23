---
title: Classe SqlServerAlias | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- SqlServerAlias Class
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SqlServerAlias class
ms.assetid: 475662b9-6985-45bf-b1e9-b0f26ef50443
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 01e66c9362a8e1c91bd43e4d6821e12f93d23152
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044479"
---
# <a name="sqlserveralias-class"></a>Classe SqlServerAlias
  La [classe SqlServerAlias](sqlserveralias-class.md) représente un alias de connexion au serveur.  
  
 Un alias de connexion au serveur est requis lorsque les deux conditions suivantes sont remplies :  
  
-   le client se connecte à une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur un transport réseau qui n'est pas le transport réseau par défaut ;  
  
-   l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à laquelle le client est connecté écoute sur un autre canal nommé.  
  
 **Remarque :** le [classe SqlServerAlias](sqlserveralias-class.md) hérite la `Put` méthode à partir de la classe de fournisseur. Toutefois, elle ne retourne pas de résultats comme indiqué par la méthode `Provider::Put`. Pour plus d'informations, consultez la documentation relative à WMI.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer des protocoles clients](http://technet.microsoft.com/library/ms181035.aspx)  
  
  