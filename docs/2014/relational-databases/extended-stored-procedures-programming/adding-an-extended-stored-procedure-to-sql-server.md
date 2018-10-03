---
title: Ajout d’une étendue procédure stockée pour SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], adding
- adding extended stored procedures
- collations [SQL Server], extended stored procedures
ms.assetid: 10f1bb74-3b43-4efd-b7ab-7a85a8600a50
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8ec7501a3a1d554d3437ea37f208f60fc66555f8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191549"
---
# <a name="adding-an-extended-stored-procedure-to-sql-server"></a>Ajout d'une procédure stockée étendue à SQL Server
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Une DLL qui contient des fonctions de procédure stockée étendue joue le rôle d'extension pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour installer la DLL, copiez le fichier vers un répertoire, tel que celui qui contient la norme [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fichiers DLL (C:\Program Files\Microsoft SQL Server\MSSQL12.0. *x*\MSSQL\Binn par défaut).  
  
 Une fois la DLL de procédure stockée étendue copiée vers le serveur, un administrateur système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit inscrire dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] chaque fonction de procédure stockée étendue dans la DLL. Vous devez pour cela utiliser la procédure stockée système sp_addextendedproc.  
  
> [!IMPORTANT]  
>  Il est conseillé à l'administrateur système de vérifier minutieusement la procédure stockée étendue afin de s'assurer qu'elle ne contient aucun code nuisible ou malveillant avant de l'ajouter au serveur et d'accorder à d'autres utilisateurs des autorisations d'exécution.  Validez toutes les entrées utilisateur. Ne concaténez pas les entrées d’utilisateur avant de valider. N'exécutez jamais une commande élaborée à partir d'une entrée utilisateur non validée.  
  
 Le premier paramètre de sp_addextendedproc spécifie le nom de la fonction et le deuxième paramètre spécifie le nom de la DLL dans laquelle cette fonction réside. Il est recommandé de spécifier le chemin complet d'accès à la DLL.  
  
> [!IMPORTANT]  
>  Les DLL existantes qui n'ont pas été inscrites avec un chemin d'accès complet ne fonctionneront plus après une mise à niveau vers SQL Server 2005 ou version ultérieure. Pour corriger ce problème, utilisez sp_dropextendedproc pour annuler l'inscription de la DLL, puis inscrivez-la de nouveau avec la procédure sp_addextendedproc, en spécifiant le chemin d'accès complet.  
  
 Le nom de la fonction spécifié dans `sp_addextendedproc` doit être exactement identique (y compris la casse) au nom de la fonction dans la DLL. Par exemple, cette commande inscrit une fonction `xp_hello,` située dans une DLL nommée `xp_hello.dll`, en tant que procédure stockée étendue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
```  
sp_addextendedproc 'xp_hello', 'c:\Program Files\Microsoft SQL Server\MSSQL12.0.MSSQLSERVER\MSSQL\Binn\xp_hello.dll';  
```  
  
 Si le nom de la fonction spécifié dans `sp_addextendedproc` ne correspond pas exactement au nom de fonction dans la DLL, le nouveau nom sera inscrit dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais le nom ne sera pas utilisable. Par exemple, bien que `xp_Hello` est inscrit comme un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] située dans procédure stockée étendue `xp_hello.dll`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne sera pas en mesure de trouver la fonction dans la DLL si vous utilisez `xp_Hello` pour appeler la fonction ultérieurement.  
  
```  
--Register the function (xp_hello) with an initial upper case  
sp_addextendedproc 'xp_Hello', 'c:\xp_hello.dll';  
  
--Use the newly registered name to call the function  
DECLARE @txt varchar(33);  
EXEC xp_Hello @txt OUTPUT;  
  
--This is the error message  
Server: Msg 17750, Level 16, State 1, Procedure xp_Hello, Line 1  
Could not load the DLL xp_hello.dll, or one of the DLLs it references. Reason: 127(The specified procedure could not be found.).  
```  
  
 Si le nom de la fonction spécifié dans `sp_addextendedproc` correspond exactement au nom de fonction dans la DLL et que le classement de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas sensible à la casse, l'utilisateur peut appeler la procédure stockée étendue à l'aide de toute combinaison de lettres minuscules et majuscules du nom.  
  
```  
--Register the function (xp_hello)  
sp_addextendedproc 'xp_hello', 'c:\xp_hello.dll';  
  
--The following will succeed in calling xp_hello  
DECLARE @txt varchar(33);  
EXEC xp_Hello @txt OUTPUT;  
  
DECLARE @txt varchar(33);  
EXEC xp_HelLO @txt OUTPUT;  
  
DECLARE @txt varchar(33);  
EXEC xp_HELLO @txt OUTPUT;  
```  
  
 Lorsque le classement de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] respecte la casse, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne sera pas en mesure d'appeler la procédure stockée étendue (même si elle a été inscrite avec exactement les mêmes nom et classement que la fonction dans la DLL) si la procédure est appelée avec une casse différente.  
  
```  
--Register the function (xp_hello)  
sp_addextendedproc 'xp_hello', 'c:\xp_hello.dll';  
  
--The following will result in an error  
DECLARE @txt varchar(33);  
EXEC xp_HELLO @txt OUTPUT;  
  
--This is the error  
Server: Msg 2812, Level 16, State 62, Line 1  
```  
  
 Il n'est pas nécessaire d'arrêter et de redémarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
