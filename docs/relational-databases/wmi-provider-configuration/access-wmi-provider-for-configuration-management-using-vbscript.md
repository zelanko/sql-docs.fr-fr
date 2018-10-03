---
title: Modifier les propriétés SQL Server Service avancées à l’aide de VBScript | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- VBScript [WMI]
- modifying SQL Server Service properties
- WMI Provider for Configuration Management, VBScript
ms.assetid: f3c5d981-eaa3-4d34-9b91-37e42636aa81
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 60dc69dfa0077c5adc375aa11eba411ab4004345
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47802097"
---
# <a name="access-wmi-provider-for-configuration-management-using-vbscript"></a>Accéder au fournisseur WMI pour la gestion de la configuration à l’aide de VBScript
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Cette section décrit comment créer un programme VBScript qui répertorie les versions des instances installées de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui s’exécutent sur un ordinateur.  
  
 L'exemple de code répertorie les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui s'exécutent sur l'ordinateur et leur version.  
  
### <a name="listing-name-and-version-of-installed-instances-of-sql-server"></a>Liste des noms et versions des instances installées de SQL Server  
  
1.  Ouvrez un nouveau document dans un éditeur de texte, tel que le Bloc-notes [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Copiez le code qui suit cette procédure et enregistrez le fichier avec une extension .vbs. Cet exemple est appelé test.vbs.  
  
2.  Connectez-vous à une instance du fournisseur WMI pour Gestion de l'ordinateur avec la fonction VBScript `GetObject`. Cet exemple se connecte à un ordinateur distant nommé mpc, mais omet le nom d'ordinateur pour se connecter à l'ordinateur local : winmgmts:root\Microsoft\SqlServer\ComputerManagement. Pour plus d'informations sur la fonction `GetObject`, consultez les informations de référence sur VBScript.  
  
3.  Utilisez la méthode `InstancesOf` pour dresser la liste des services. Ces services peuvent également être énumérés à l'aide d'une requête WQL simple et d'une méthode `ExecQuery` à la place d'une méthode `InstancesOf`.  
  
4.  Utilisez la méthode `ExecQuery` et une requête WQL pour extraire le nom et la version des instances installées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  Enregistrez le fichier.  
  
6.  Exécutez le script en tapant **cscript test.vbs** à l’invite de commandes.  
  
## <a name="example"></a>Exemple  
  
```  
set wmi = GetObject("WINMGMTS:\\.\root\Microsoft\SqlServer\ComputerManagement12")  
for each prop in wmi.ExecQuery("select * from SqlServiceAdvancedProperty where SQLServiceType = 1 AND PropertyName = 'VERSION'")  
WScript.Echo prop.ServiceName & " " & prop.PropertyName & ": " & prop.PropertyStrValue  
next  
```  
  
  
