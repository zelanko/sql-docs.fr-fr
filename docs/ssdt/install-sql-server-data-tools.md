---
title: Installer les outils de données SQL Server Data Tools | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.package.stub
ms.assetid: 6f8616cb-9119-42c3-a9b1-936e088763e7
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2df3214ce5ae02e4feb076f77e66b153c4d2abdb
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39088021"
---
# <a name="install-sql-server-data-tools"></a>Installer les outils de données SQL Server
Cette rubrique décrit comment installer SQL Server Data Tools. Les mises à jour vers SQL Server Data Tools sont disponibles dans la page de téléchargement de SQL Server Data Tools ([Installer la dernière version de SQL Server Data Tools](http://go.microsoft.com/fwlink/?LinkID=616714)).  
  
Que vous utilisiez Visual Studio 2012 ou Visual Studio 2013, vous devez installer les mises à jour les plus récentes de SQL Server Data Tools pour obtenir les dernières fonctionnalités.  
  
## <a name="sql-server-data-tools-for-visual-studio-2013"></a>SQL Server Data Tools pour Visual Studio 2013  
SQL Server Data Tools est fourni avec Visual Studio 2013 Express pour le Web, Visual Studio 2013 Express pour le Bureau, Visual Studio Community 2013, ainsi que tous les SKU payants, y compris le SKU Professional et versions ultérieures. Après avoir installé Visual Studio 2013, vous pouvez accéder à Outils -> Extensions et mises à jour -> Mises à jour pour savoir s'il existe une mise à jour à installer.  
  
## <a name="sql-server-data-tools-for-visual-studio-2012"></a>SQL Server Data Tools pour Visual Studio 2012  
SQL Server Data Tools est fourni avec la référence SKU professionnelle de Visual Studio 2012 ou une version ultérieure. Après que vous avez installé Visual Studio 2012 et la mise à jour de SQL Server Data Tools de novembre 2012 ou une version ultérieure, SQL Server Data Tools peut générer un rapport lorsqu’une mise à jour doit être installée. Pour plus d'informations, consultez [Boîte de dialogue Rechercher des mises à jour](../ssdt/check-for-updates-dialog-box.md).  
  
Si Visual Studio 2012 n’est pas installé, SQL Server Data Tools installera le Shell intégré de Visual Studio 2012 et SQL Server Data Tools.  
  
## <a name="administrative-installation-point"></a>Point d'installation d'administration  
Si vous devez installer SQL Server Data Tools sur plusieurs ordinateurs qui n'ont pas accès à Internet, créez une disposition d'installation d'administration sur un partage réseau ou un support physique, puis procédez à l'installation à partir de ce point d'installation.  
  
Pour créer une disposition d'installation, téléchargez le fichier SSDTSetup.EXE et exécutez-le avec l'option `/layout`*emplacement* pour créer une disposition à *emplacement*. Les utilisateurs peuvent ensuite exécuter SSDTSetup.Exe à partir d' *emplacement*.  
  
Pour télécharger SSDTSetup.exe, accédez à [Installer la dernière version de SQL Server Data Tools](http://go.microsoft.com/fwlink/?LinkID=616714), cliquez sur le lien correspondant à votre version de Visual Studio, puis téléchargez SSDTSetup.exe pour votre langue.  
  
