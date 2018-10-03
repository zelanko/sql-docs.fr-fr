---
title: Classe SqlServerAlias | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apiname:
- SqlServerAlias Class
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SqlServerAlias class
ms.assetid: 475662b9-6985-45bf-b1e9-b0f26ef50443
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 75ca27fc8c035a2b62cc70bbf740dd746f341d45
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47603527"
---
# <a name="sqlserveralias-class"></a>Classe SqlServerAlias
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  La [classe SqlServerAlias](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) représente un alias de connexion au serveur.  
  
 Un alias de connexion au serveur est requis lorsque les deux conditions suivantes sont remplies :  
  
-   le client se connecte à une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur un transport réseau qui n'est pas le transport réseau par défaut ;  
  
-   l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à laquelle le client est connecté écoute sur un autre canal nommé.  
  
 **Remarque :** la [classe SqlServerAlias](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) hérite la méthode **Put** de la classe Provider. Toutefois, elle ne retourne pas de résultats comme indiqué par la méthode **Provider::Put** . Pour plus d'informations, consultez la documentation relative à WMI.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer des protocoles clients](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
