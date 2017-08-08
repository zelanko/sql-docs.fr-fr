---
title: "Télécharger le module PowerShell SQL Server | Microsoft Docs"
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
- "installer powershell sql server, télécharger powershell sql server"
ms.assetid: 
caps.latest.revision: 113
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: b68d454230d414ff52d90b4f3f71dd68ee65c6bc
ms.openlocfilehash: f55266b6ec28e2552047cc36a5060945006b2caa
ms.contentlocale: fr-fr
ms.lasthandoff: 07/31/2017

---
# <a name="download-sql-server-powershell-module"></a>Télécharger le module PowerShell SQL Server
Le module PowerShell SQL Server fait partie de la version 17.0 de SQL Server Management Studio et il est désormais fourni via PowerShell Gallery.  Le module n’est plus inclus dans le package d’installation de SSMS. Pour utiliser PowerShell avec SSMS 17.0 et ultérieur, vous devez en plus installer le module SQL Server sur l’ordinateur.

Vous pouvez trouver une documentation complète sur l’installation de la dernière version de Windows Management Framework et sur l’installation en général des modules PowerShell sur le site [PowerShell Gallery](https://www.powershellgallery.com/).

La commande PowerShell pour installer le module SQL Server est :

> Install-module -Name SqlServer -Scope CurrentUser

S’il existe des versions antérieures des modules PowerShell SQL Server sur la machine, il peut être nécessaire d’ajouter le paramètre «-AllowClobber ».  

Les versions du module PowerShell SQL Server incluses dans PowerShell Gallery prennent en charge la gestion de versions et nécessitent PowerShell version 5.0 ou ultérieure.

