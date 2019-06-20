---
title: Modifier les propriétés SQL Server Service avancées à l’aide de VBScript | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
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
ms.openlocfilehash: f3a380f80b4ecc7540e29605543722edd55e226d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62705065"
---
# <a name="modify-sql-server-service-advanced-properties-using-vbscript"></a>Modifier les propriétés avancées du service SQL Server à l'aide de VBScript
  Cette section décrit comment créer un programme VBScript qui répertorie les versions des instances installées de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui s’exécutent sur un ordinateur.  
  
 L'exemple de code répertorie les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui s'exécutent sur l'ordinateur et leur version.  
  
### <a name="listing-name-and-version-of-installed-instances-of-sql-server"></a>Liste des noms et versions des instances installées de SQL Server  
  
1.  Ouvrez un nouveau document dans un éditeur de texte, tel que le Bloc-notes [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Copiez le code qui suit cette procédure et enregistrez le fichier avec une extension .vbs. Cet exemple est appelé test.vbs.  
  
2.  Connectez-vous à une instance du fournisseur WMI pour Gestion de l'ordinateur avec la fonction VBScript `GetObject`. Cet exemple se connecte à un ordinateur distant nommé mpc, mais omet le nom d'ordinateur pour se connecter à l'ordinateur local : winmgmts:root\Microsoft\SqlServer\ComputerManagement. Pour plus d'informations sur la fonction `GetObject`, consultez les informations de référence sur VBScript.  
  
3.  Utilisez la méthode `InstancesOf` pour dresser la liste des services. Ces services peuvent également être énumérés à l'aide d'une requête WQL simple et d'une méthode `ExecQuery` à la place d'une méthode `InstancesOf`.  
  
4.  Utilisez la méthode `ExecQuery` et une requête WQL pour extraire le nom et la version des instances installées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  Enregistrez le fichier.  
  
6.  Exécutez le script en tapant `cscript test.vbs` à l’invite de commandes.  
  
## <a name="example"></a>Exemple  
  
```  
set wmi = GetObject("WINMGMTS:\\.\root\Microsoft\SqlServer\ComputerManagement12")  
for each prop in wmi.ExecQuery("select * from SqlServiceAdvancedProperty where SQLServiceType = 1 AND PropertyName = 'VERSION'")  
WScript.Echo prop.ServiceName & " " & prop.PropertyName & ": " & prop.PropertyStrValue  
next  
```  
  
  
