---
title: Modification des mots de passe par programme | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.reviewer: ''
ms.prod: sql
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], password expiration
- SQL Server Native Client ODBC driver, passwords
- SQL Server Native Client OLE DB provider, passwords
- passwords [SQL Server], expiration
- SQLNCLI, password expiration
- expiration [SQL Server Native Client]
- passwords [SQL Server], modifying
- expired passwords [SQL Server Native Client]
- SQL Server Native Client, password expiration
- modifying passwords
ms.assetid: 624ad949-5fed-4ce5-b319-878549f9487b
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f4bada5561a4e9af4b779ea26c13fac7ea57dad2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303847"
---
# <a name="changing-passwords-programmatically"></a>Modification des mots de passe par programme
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Avant [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], lorsque le mot de passe d'un utilisateur expirait, seul un administrateur pouvait le réinitialiser. Commençant [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , Native Client prend en charge [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] le traitement de l’expiration du mot de passe programmatiquement par l’intermédiaire du fournisseur de DB OLE de client autochtone et du [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] chauffeur native ODBC, et par des changements aux boîtes de dialogue **SQL Server Login.**  
  
> [!NOTE]  
>  Si possible, demandez aux utilisateurs de saisir leurs informations d'identification au moment de l'exécution et éviter de les stocker leurs références dans un format permanent. Si vous devez conserver les informations d’identification, chiffrez-les avec [l’API de chiffrement Win32](https://go.microsoft.com/fwlink/?LinkId=64532). Pour plus d’informations sur l’utilisation des mots de passe, consultez [Mots de passe forts](../../../relational-databases/security/strong-passwords.md).  
  
## <a name="sql-server-login-error-codes"></a>Codes d'erreur des connexions SQL Server  
 Lorsqu'une connexion ne peut pas être établie en raison de problèmes d'authentification, l'un des codes d'erreur SQL Server suivants est disponible pour aider l'application à établir le diagnostic et la récupération.  
  
|Code d'erreur SQL Server|Message d’erreur|  
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
  
## <a name="sql-server-native-client-ole-db-provider"></a>Fournisseur OLE DB SQL Server Native Client  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur native Client OLE DB prend en charge l’expiration du mot de passe par une interface utilisateur et de manière programmatique.  
  
### <a name="ole-db-user-interface-password-expiration"></a>Expiration du mot de passe de l'interface utilisateur OLE DB  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur native Client OLE DB prend en charge l’expiration du mot de passe par des modifications apportées aux boîtes de dialogue **SQL Server Login.** Si la valeur de DBPROP_INIT_PROMPT est définie sur DBPROMPT_NOPROMPT, la tentative de connexion initiale échoue si le mot de passe a expiré.  
  
 Si DBPROP_INIT_PROMPT a été défini sur une autre valeur, l’utilisateur voit la boîte de dialogue de **compte de connexion SQL Server**, que le mot de passe ait expiré ou non. L’utilisateur peut cliquer sur le bouton **Options** et cocher **Changer le mot de passe** pour modifier le mot de passe.  
  
 Si l’utilisateur clique sur OK et que le mot de passe a expiré, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] invite l’utilisateur à entrer et à confirmer un nouveau mot de passe à l’aide de la boîte de dialogue **Changement de mot de passe SQL Server**.  
  
#### <a name="ole-db-prompt-behavior-and-locked-accounts"></a>Comportement d'invite OLE DB et comptes verrouillés  
 Les tentatives de connexion peuvent échouer en raison du compte verrouillé. Si cela se produit après l’affichage de la boîte de dialogue de **compte de connexion SQL Server**, le message d’erreur du serveur s’affiche pour l’utilisateur et la tentative de connexion est abandonnée. Cette situation peut aussi avoir lieu après l’affichage de la boîte de dialogue **Changement de mot de passe SQL Server** si l’utilisateur entre une valeur incorrecte pour l’ancien mot de passe. Dans ce cas le même message d'erreur s'affiche et la tentative de connexion est abandonnée.  
  
#### <a name="ole-db-connection-pooling-password-expiration-and-locked-accounts"></a>Regroupement de connexions OLE DB, expiration de mot de passe et comptes verrouillés  
 Un compte peut être verrouillé ou son mot de passe peut expirer pendant que la connexion est toujours active dans un pool de connexions. Le serveur contrôle les mots de passe périmés et les comptes verrouillés en deux occasions. La première occasion correspond au moment de la création de la connexion. La seconde occasion se produit lors de la réinitialisation de la connexion, quand la connexion est extraite du pool.  
  
 Quand la tentative de réinitialisation échoue, la connexion est supprimée du pool et une erreur est retournée.  
  
### <a name="ole-db-programmatic-password-expiration"></a>Expiration de mot de passe par programmation OLE DB  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur de DB OLE native Client prend en charge l’expiration du mot de passe par l’ajout de la propriété SSPROP_AUTH_OLD_PASSWORD (type VT_BSTR) qui a été ajoutée à l’ensemble de propriétés DBPROPSET_SQLSERVERDBINIT.  
  
 La propriété « Mot de passe » existante se rapporte à DBPROP_AUTH_PASSWORD et est utilisée pour stocker le nouveau mot de passe.  
  
> [!NOTE]  
>  Dans la chaîne de connexion, la propriété « Ancien Mot de passe » définit SSPROP_AUTH_OLD_PASSWORD, qui correspond au mot de passe en cours (peut-être périmé) qui n'est pas disponible via une propriété de chaîne de fournisseur.  
  
 Le fournisseur ne rend pas la valeur de cette propriété persistante. Lorsque cette propriété est définie, le fournisseur n'utilise pas le pool de connexions de la première connexion, sinon une nouvelle connexion interviendra. Si la modification de mot de passe est réussie, la connexion actuelle ne peut pas être réutilisée, car elle contient toujours l'ancien mot de passe, qui ne sera pas valide après la modification. Également, si la connexion réussit, le fournisseur efface la propriété. Les tentatives suivantes d'extraction de l'ancien mot de passe retournent VT_EMPTY.  
  
> [!NOTE]  
>  SSPROP_AUTH_OLD_PASSWORD ne doit jamais être rendu persistant, car il n'est utilisé que lorsqu'un mot de passe a expiré.  
  
 Notez que chaque fois que la propriété « Ancien Mot de passe » propriété est définie, le fournisseur suppose qu'une tentative de modification du mot de passe a lieu, à moins que l'authentification Windows ne soit également spécifiée, dans quel cas elle est toujours prioritaire.  
  
 Si l’authentification Windows est utilisée, la spécification de l’ancien mot de passe se traduit par DB_E_ERRORSOCCURRED ou DB_S_ERRORSOCCURRED, selon que l’ancien mot de passe a respectivement été spécifié comme REQUIRED ou OPTIONAL, et que la valeur d’état de DBPROPSTATUS_CONFLICTINGBADVALUE est retournée dans *dwStatus*. Cela est détecté quand **IDBInitialize::Initialize** est appelée.  
  
 Si une tentative de modifier le mot de passe échoue de façon inattendue, le serveur retourne le code d'erreur 18468. Une erreur OLEDB standard est retournée à partir de la tentative de connexion.  
  
 Pour plus d'informations sur le jeu de propriétés DBPROPSET_SQLSERVERDBINIT, consultez [Propriétés d'initialisation et d'autorisation](../../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
## <a name="sql-server-native-client-odbc-driver"></a>Pilote ODBC SQL Server Native Client  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur native Client OLE DB prend en charge l’expiration du mot de passe par une interface utilisateur et de manière programmatique.  
  
### <a name="odbc-user-interface-password-expiration"></a>Expiration du mot de passe de l'interface utilisateur ODBC  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] conducteur native De l’ODBC prend en charge l’expiration du mot de passe par des modifications apportées aux boîtes de dialogue **SQL Server Login.**  
  
 Si [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) est appelé et que la valeur de **DriverCompletion** est réglée pour SQL_DRIVER_NOPROMPT, la tentative de connexion initiale échoue si le mot de passe a expiré. La valeur SQLSTATE 28000 et la valeur du code d’erreur native 18487 sont retournées par des appels ultérieurs à **SQLError** ou **SQLGetDiagRec**.  
  
 Si **DriverCompletion** a été réglé à toute autre valeur, l’utilisateur voit le dialogue **SQL Server Login,** que le mot de passe ait expiré ou non. L’utilisateur peut cliquer sur le bouton **Options** et cocher **Changer le mot de passe** pour modifier le mot de passe.  
  
 Si l’utilisateur clique sur OK [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et que le mot de passe a expiré, invite à entrer et confirmer un nouveau mot de passe à l’aide du dialogue **changeur de mot de passe du serveur SQL.**  
  
#### <a name="odbc-prompt-behavior-and-locked-accounts"></a>Comportement d'invite ODBC et comptes verrouillés  
 Les tentatives de connexion peuvent échouer en raison du compte verrouillé. Si cela se produit après l’affichage de la boîte de dialogue de **compte de connexion SQL Server**, le message d’erreur du serveur s’affiche pour l’utilisateur et la tentative de connexion est abandonnée. Cette situation peut aussi avoir lieu après l’affichage de la boîte de dialogue **Changement de mot de passe SQL Server** si l’utilisateur entre une valeur incorrecte pour l’ancien mot de passe. Dans ce cas le même message d'erreur s'affiche et la tentative de connexion est abandonnée.  
  
#### <a name="odbc-connection-pooling-password-expiry-and-locked-accounts"></a>Regroupement de connexions ODBC, expiration de mot de passe et comptes verrouillés  
 Un compte peut être verrouillé ou son mot de passe peut expirer pendant que la connexion est toujours active dans un pool de connexions. Le serveur contrôle les mots de passe périmés et les comptes verrouillés en deux occasions. La première occasion correspond au moment de la création de la connexion. La seconde occasion se produit lors de la réinitialisation de la connexion, quand la connexion est extraite du pool.  
  
 Quand la tentative de réinitialisation échoue, la connexion est supprimée du pool et une erreur est retournée.  
  
### <a name="odbc-programmatic-password-expiration"></a>Expiration de mot de passe par programmation ODBC  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote Native Client ODBC prend en charge l’expiration du mot de passe grâce à l’ajout de l’attribut SQL_COPT_SS_OLDPWD qui est défini avant de se connecter au serveur à l’aide de la fonction [SQLSetConnectAttr.](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)  
  
 L'attribut SQL_COPT_SS_OLDPWD du handle de connexion fait référence au mot de passe périmé. Il n'existe aucun attribut de chaîne de connexion pour cet attribut, car il entraînerait une interférence avec le regroupement de connexions. Si la connexion réussit, le pilote efface cet attribut.  
  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote Native Client ODBC retourne SQL_ERROR dans quatre cas pour cette fonctionnalité : expiration du mot de passe, conflit de stratégie de mot de passe, lock-out de compte, et lorsque l’ancienne propriété de mot de passe est définie lors de l’utilisation de Windows Authentication. Le conducteur renvoie les messages d’erreur appropriés à l’utilisateur lorsque [SQLGetDiagField](../../../relational-databases/native-client-odbc-api/sqlgetdiagfield.md) est invoqué.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
