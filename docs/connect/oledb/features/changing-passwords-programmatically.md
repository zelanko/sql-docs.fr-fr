---
title: Modification des mots de passe par programmation | Microsoft Docs
description: Modification des mots de passe par programmation à l’aide de OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], password expiration
- OLE DB Driver for SQL Server, passwords
- passwords [SQL Server], expiration
- MSOLEDBSQL, password expiration
- expiration [OLE DB Driver for SQL Server]
- passwords [SQL Server], modifying
- expired passwords [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, password expiration
- modifying passwords
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: a37f5a10f6b594a00c068fd61be1b7903bd097cc
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43024568"
---
# <a name="changing-passwords-programmatically"></a>Modification des mots de passe par programme
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Avant [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], lorsque le mot de passe d'un utilisateur expirait, seul un administrateur pouvait le réinitialiser. À partir de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], OLE DB Driver pour SQL Server prend en charge la gestion d’expiration de mot de passe par programmation via le pilote OLE DB et via les modifications du **connexion à SQL Server** boîtes de dialogue.  
  
> [!NOTE]  
>  Si possible, demandez aux utilisateurs de saisir leurs informations d'identification au moment de l'exécution et éviter de les stocker leurs références dans un format permanent. Si vous devez conserver les informations d’identification, chiffrez-les avec [l’API de chiffrement Win32](http://go.microsoft.com/fwlink/?LinkId=64532). Pour plus d’informations sur l’utilisation des mots de passe, consultez [Mots de passe forts](../../../relational-databases/security/strong-passwords.md).  
  
## <a name="sql-server-login-error-codes"></a>Codes d'erreur des connexions SQL Server  
 Lorsqu'une connexion ne peut pas être établie en raison de problèmes d'authentification, l'un des codes d'erreur SQL Server suivants est disponible pour aider l'application à établir le diagnostic et la récupération.  
  
|Code d'erreur SQL Server|Message d'erreur|  
|---------------------------|-------------------|  
|15113|La connexion a échoué pour l'utilisateur '%.*ls' Motif : échec de la validation du mot de passe. Le compte est verrouillé.|  
|18463|Échec de l'ouverture de session pour l'utilisateur '%.*ls'. Raison : échec de changement de mot de passe. Impossible d'utiliser le mot de passe pour l'instant.|  
|18464|Échec de l'ouverture de session pour l'utilisateur '%.*ls'. Raison : échec de changement de mot de passe. Ce mot de passe ne répond pas aux exigences de la stratégie, car il est trop court.|  
|18465|Échec de l'ouverture de session pour l'utilisateur '%.*ls'. Raison : échec de changement de mot de passe. Ce mot de passe ne répond pas aux exigences de la stratégie, car il est trop long.|  
|18466|Échec de l'ouverture de session pour l'utilisateur '%.*ls'. Raison : échec de changement de mot de passe. Ce mot de passe ne répond pas aux exigences de la stratégie, car il n'est pas assez complexe.|  
|18467|Échec de l'ouverture de session pour l'utilisateur '%.*ls'. Raison : échec de changement de mot de passe. Le mot de passe ne répond pas aux exigences de la DLL de filtre de mots de passe.|  
|18468|Échec de l'ouverture de session pour l'utilisateur '%.*ls'. Raison : échec de changement de mot de passe. Une erreur inattendue s'est produite lors de la validation de mot de passe.|  
|18487|Échec de l'ouverture de session pour l'utilisateur '%.*ls'. Raison : le mot de passe associé à ce compte a expiré.|  
|18488|Échec de l'ouverture de session pour l'utilisateur '%.*ls'. Raison : le mot de passe du compte doit être changé.|  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver pour SQL Server  
 Le pilote OLE DB pour SQL Server prend en charge l’expiration du mot de passe via une interface utilisateur et par programme.  
  
### <a name="ole-db-user-interface-password-expiration"></a>Expiration du mot de passe de l'interface utilisateur OLE DB  
 OLE DB Driver pour SQL Server prend en charge l’expiration de mot de passe par les modifications effectuées dans les boîtes de dialogue de **compte de connexion SQL Server**. Si la valeur de DBPROP_INIT_PROMPT est définie sur DBPROMPT_NOPROMPT, la tentative de connexion initiale échoue si le mot de passe a expiré.  
  
 Si DBPROP_INIT_PROMPT a été défini sur une autre valeur, l’utilisateur voit la boîte de dialogue de **compte de connexion SQL Server**, que le mot de passe ait expiré ou non. L’utilisateur peut cliquer sur le bouton **Options** et cocher **Changer le mot de passe** pour modifier le mot de passe.  
  
 Si l’utilisateur clique sur OK et que le mot de passe a expiré, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] invite l’utilisateur à entrer et à confirmer un nouveau mot de passe à l’aide de la boîte de dialogue **Changement de mot de passe SQL Server**.  
  
#### <a name="ole-db-prompt-behavior-and-locked-accounts"></a>Comportement d'invite OLE DB et comptes verrouillés  
 Les tentatives de connexion peuvent échouer en raison du compte verrouillé. Si cela se produit après l’affichage de la boîte de dialogue de **compte de connexion SQL Server**, le message d’erreur du serveur s’affiche pour l’utilisateur et la tentative de connexion est abandonnée. Cette situation peut aussi avoir lieu après l’affichage de la boîte de dialogue **Changement de mot de passe SQL Server** si l’utilisateur entre une valeur incorrecte pour l’ancien mot de passe. Dans ce cas le même message d'erreur s'affiche et la tentative de connexion est abandonnée.  
  
#### <a name="ole-db-connection-pooling-password-expiration-and-locked-accounts"></a>Regroupement de connexions OLE DB, expiration de mot de passe et comptes verrouillés  
 Un compte peut être verrouillé ou son mot de passe peut expirer pendant que la connexion est toujours active dans un pool de connexions. Le serveur contrôle les mots de passe périmés et les comptes verrouillés en deux occasions. La première occasion correspond au moment de la création de la connexion. La seconde occasion se produit lors de la réinitialisation de la connexion, quand la connexion est extraite du pool.  
  
 Quand la tentative de réinitialisation échoue, la connexion est supprimée du pool et une erreur est retournée.  
  
### <a name="ole-db-programmatic-password-expiration"></a>Expiration de mot de passe par programmation OLE DB  
 OLE DB Driver pour SQL Server prend en charge l’expiration de mot de passe par l’ajout de la propriété SSPROP_AUTH_OLD_PASSWORD (type VT_BSTR) au jeu de propriétés DBPROPSET_SQLSERVERDBINIT.  
  
 La propriété « Mot de passe » existante se rapporte à DBPROP_AUTH_PASSWORD et est utilisée pour stocker le nouveau mot de passe.  
  
> [!NOTE]  
>  Dans la chaîne de connexion, la propriété « Ancien Mot de passe » définit SSPROP_AUTH_OLD_PASSWORD, qui correspond au mot de passe en cours (peut-être périmé) qui n'est pas disponible via une propriété de chaîne de fournisseur.  
  
 Le fournisseur ne rend pas la valeur de cette propriété persistante. Lorsque cette propriété est définie, le fournisseur n'utilise pas le pool de connexions de la première connexion, sinon une nouvelle connexion interviendra. Si la modification de mot de passe est réussie, la connexion actuelle ne peut pas être réutilisée, car elle contient toujours l'ancien mot de passe, qui ne sera pas valide après la modification. Également, si la connexion réussit, le fournisseur efface la propriété. Les tentatives suivantes d'extraction de l'ancien mot de passe retournent VT_EMPTY.  
  
> [!NOTE]  
>  SSPROP_AUTH_OLD_PASSWORD ne doit jamais être rendu persistant, car il n'est utilisé que lorsqu'un mot de passe a expiré.  
  
 Notez que chaque fois que la propriété « Ancien Mot de passe » propriété est définie, le fournisseur suppose qu'une tentative de modification du mot de passe a lieu, à moins que l'authentification Windows ne soit également spécifiée, dans quel cas elle est toujours prioritaire.  
  
 Si l’authentification Windows est utilisée, la spécification de l’ancien mot de passe se traduit par DB_E_ERRORSOCCURRED ou DB_S_ERRORSOCCURRED, selon que l’ancien mot de passe a respectivement été spécifié comme REQUIRED ou OPTIONAL, et que la valeur d’état de DBPROPSTATUS_CONFLICTINGBADVALUE est retournée dans *dwStatus*. Cela est détecté quand **IDBInitialize::Initialize** est appelée.  
  
 Si une tentative de modifier le mot de passe échoue de façon inattendue, le serveur retourne le code d'erreur 18468. Une erreur OLEDB standard est retournée à partir de la tentative de connexion.  
  
 Pour plus d’informations sur le jeu de propriétés DBPROPSET_SQLSERVERDBINIT, consultez [propriétés d’initialisation et d’autorisation](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md).  

  
## <a name="see-also"></a> Voir aussi  
 [Fonctionnalités OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
