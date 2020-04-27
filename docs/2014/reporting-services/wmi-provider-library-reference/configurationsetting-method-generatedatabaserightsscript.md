---
title: GenerateDatabaseRightsScript, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseRightsScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseRightsScript method
ms.assetid: f2e6dcc9-978f-4c2c-bafe-36c330247fd0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 575eab878e0ef9b4357c09a0a3deedf143c237b9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66098481"
---
# <a name="generatedatabaserightsscript-method-wmi-msreportserver_configurationsetting"></a>Méthode GenerateDatabaseRightsScript (WMI MSReportServer_ConfigurationSetting)
  Génère un script SQL pouvant être utilisé pour accorder des droits d'utilisateur à la base de données du serveur de rapports et à d'autres bases de données requises pour l'exécution d'un serveur de rapports. Il est prévu que l'appelant se connecte au serveur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et exécute le script.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub GenerateDatabaseRightsScript(ByVal UserName As String, _  
    ByVal DatabaseName As String, ByVal IsRemote As Boolean, _  
    ByVal IsWindowsUser As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseRightsScript(string UserName, string DatabaseName, bool IsRemote, bool IsWindowsUser, out string Script,   
out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *UserName*  
 Nom d'utilisateur ou identificateur de sécurité Windows (SID) de l'utilisateur auquel le script accorde des droits.  
  
 *DatabaseName*  
 Nom de la base de données à laquelle le script accordera l'accès à l'utilisateur.  
  
 *IsRemote*  
 Valeur booléenne indiquant si la base de données est distante du serveur de rapports.  
  
 *IsWindowsUser*  
 Valeur booléenne qui indique si le nom d'utilisateur spécifié est un utilisateur Windows ou un utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 *Script*  
 [out] Chaîne contenant le script [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] généré.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes  
 Si *DatabaseName* est vide, *IsRemote* est ignoré et la valeur du fichier de configuration du serveur de rapports est utilisée comme nom de base de données.  
  
 Si *IsWindowsUser* a la valeur `true`, le *nom d’utilisateur* doit être \<au format \\ domaine>\><nom d’utilisateur.  
  
 Lorsque *IsWindowsUser* a la valeur `true`, le script généré accorde des droits de connexion à l’utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]pour le, en définissant la base de données du serveur de rapports comme base de données par défaut et accorde le rôle **RSExec** sur la base de données du serveur de rapports, la base de données temporaire du serveur de rapports, la base de données master et la base de données système msdb.  
  
 Quand *IsWindowsUser* a la valeur `true`, la méthode accepte les SID Windows standard comme entrée. Lorsqu'un nom de compte de service ou un SID Windows standard est fourni, il est converti en une chaîne de nom d'utilisateur. Si la base de données est locale, le compte est converti en la représentation localisée correcte du compte. Si la base de données est distante, le compte est représenté en tant que compte de l’ordinateur.  
  
 Le tableau suivant répertorie les comptes qui sont convertis et indique leur représentation distante.  
  
|Compte/SID converti|Nom commun|Nom distant|  
|---------------------------------------|-----------------|-----------------|  
|(S-1-5-18)|Système Local|\<Domaine>\\<nom_ordinateur\>$|  
|.\LocalSystem|Système Local|\<Domaine>\\<nom_ordinateur\>$|  
|ComputerName\LocalSystem|Système Local|\<Domaine>\\<nom_ordinateur\>$|  
|LocalSystem|Système Local|\<Domaine>\\<nom_ordinateur\>$|  
|(S-1-5-20)|Service réseau|\<Domaine>\\<nom_ordinateur\>$|  
|NT AUTHORITY\NetworkService|Service réseau|\<Domaine>\\<nom_ordinateur\>$|  
|(S-1-5-19)|Service local|Erreur (voir ci-dessous)|  
|NT AUTHORITY\LocalService|Service local|Erreur (voir ci-dessous)|  
  
 Dans [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)], si vous utilisez un compte intégré et que la base de données du serveur de rapports est distante, une erreur est retournée.  
  
 Si le compte intégré `LocalService` est spécifié et que la base de données du serveur de rapports est distante, une erreur est retournée.  
  
 Quand *IsWindowsUser* a la valeur true et qu’il est nécessaire de convertir la valeur indiquée dans *UserName* , le fournisseur WMI détermine si la base de données du serveur de rapports réside sur le même ordinateur ou sur un ordinateur distant. Pour déterminer si l’installation est locale, le fournisseur WMI évalue la propriété DatabaseServerName par rapport à la liste de valeurs suivante. Si une correspondance est trouvée, la base de données est locale. Dans le cas contraire, elle est distante. La comparaison respecte la casse.  
  
|Valeur de DatabaseServerName|Exemple|  
|---------------------------------|-------------|  
|"."||  
|"(local)"||  
|"LOCAL"||  
|localhost||  
|\<Nom ordinateur>|labtest14|  
|\<FQDN_ordinateur>|example.redmond.microsoft.com|  
|\<Adresse IP>|180.012.345,678|  
  
 Lorsque *IsWindowsUser* a la valeur `true`, le fournisseur WMI appelle LOOKUPACCOUNTNAME pour obtenir le SID du compte, puis il appelle LookupAccountSid pour obtenir le nom à placer dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] script. De cette manière, le nom du compte utilisé réussit systématiquement la validation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Quand *IsWindowsUser* a la valeur `false`, le script généré accorde le rôle **RSExec** sur la base de données du serveur de rapports, la base de données temporaire du serveur de rapports et la base de données msdb.  
  
 Quand *IsWindowsUser* a la valeur `false`, l’utilisateur SQL Server doit déjà exister sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour que le script s’exécute correctement.  
  
 Si aucune base de données de serveur de rapports n’est spécifiée pour le serveur de rapports, l’appel de GrantRightsToDatabaseUser retourne une erreur.  
  
 Le script généré prend en charge [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 et [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
