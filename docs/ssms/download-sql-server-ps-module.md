---
title: "Télécharger le Module PowerShell SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 03/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "installer sql server powershell, téléchargez sql server powershell"
ms.assetid: 
caps.latest.revision: 113
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: b68d454230d414ff52d90b4f3f71dd68ee65c6bc
ms.openlocfilehash: f55266b6ec28e2552047cc36a5060945006b2caa
ms.contentlocale: fr-fr
ms.lasthandoff: 06/23/2017

---
# <a name="download-sql-server-powershell-module"></a>Télécharger le Module PowerShell SQL Server
Dans le cadre de la version 17,0 de SQL Server Management Studio, le module PowerShell de SQL Server est maintenant fourni via PowerShell Gallery.  Le module n’est plus inclus dans le package d’installation SSMS. Pour utiliser PowerShell avec SSMS 17,0 et les versions ultérieures, le Module SQL Server doit être installé sur l’ordinateur comme une étape supplémentaire.

Complète la documentation sur l’installation de la dernière version de Windows Management Framework et comment installer des modules PowerShell en général se trouvent sur le [PowerShell Gallery](https://www.powershellgallery.com/) site.

La commande PowerShell pour installer le module SQL Server est la suivante :

> Install-module-Name SqlServer-étendue CurrentUser

S’il existe des versions précédentes des modules PowerShell SQL Server sur l’ordinateur, il peut être nécessaire de fournir la «-AllowClobber » paramètre.  

Les versions du module PowerShell SQL Server inclus dans la galerie PowerShell prend en charge le contrôle de version et requièrent PowerShell version 5.0 ou version ultérieure.

