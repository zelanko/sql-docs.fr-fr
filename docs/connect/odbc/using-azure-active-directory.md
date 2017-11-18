---
title: "À l’aide d’Azure Active Directory avec le pilote ODBC | Documents Microsoft"
ms.custom: 
ms.date: 04/18/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52205f03-ff29-4254-bfa8-07cced155c86
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 801f0ec683811776b7a249e4984030d3496e5a1e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="using-azure-active-directory-with-the-odbc-driver"></a>À l’aide d’Azure Active Directory avec le pilote ODBC
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="purpose"></a>Fonction

ODBC Driver 13.1 for SQL Server autorise les applications ODBC pour se connecter à une instance de SQL Azure à l’aide d’une identité fédérée dans Azure Active Directory avec un nom d’utilisateur/mot de passe, un jeton d’accès Azure Active Directory (pilote Windows uniquement) ou Windows intégrée Authentification (pilote Windows uniquement). Cela s’effectue via l’utilisation de la nouvelle source de données et les mots clés de chaîne de connexion et les attributs de connexion.

## <a name="new-andor-modified-dsn-and-connection-string-keywords"></a>Source de données nouvelle ou modifiée et les mots clés de chaîne de connexion

Le `Authentication` mot clé peut être utilisé lors de la connexion avec une DSN ou chaîne de connexion pour contrôler le mode d’authentification. La valeur définie dans la chaîne de connexion qui remplace dans la source de données, si fourni. Le _valeur d’attribut préalable_ de le `Authentication` paramètre est la valeur calculée à partir de la chaîne de connexion et les valeurs de la source de données.

|Nom|Valeurs|Valeur par défaut| Description|
|-|-|-|-|
|`Authentication`|(non défini), (chaîne vide), `SqlPassword`, `ActiveDirectoryPassword`,`ActiveDirectoryIntegrated`|(non défini)|Contrôle le mode d’authentification.<table><tr><th>Valeur<th> Description<tr><td>(non défini)<td>Mode d’authentification déterminé par les autres mots clés (options de connexion d’ancienne génération existant).<tr><td>(chaîne vide)<td>(Chaîne de connexion uniquement.) Substituer et annuler un `Authentication` valeur définie dans la source de données.<tr><td>`SqlPassword`<td>S’authentifier directement à une instance de SQL Server à l’aide d’un nom d’utilisateur et un mot de passe.<tr><td>`ActiveDirectoryPassword`<td>Authentifier avec une identité Azure Active Directory à l’aide d’un nom d’utilisateur et un mot de passe.<tr><td>`ActiveDirectoryIntegrated`<td>_Seuls les pilotes Windows_. Authentifier avec une identité Azure Active Directory à l’aide de l’authentification intégrée.</table>|
|`Encrypt`|(non défini), `Yes`,`No`|(voir description)|Contrôle le chiffrement pour une connexion. Si la valeur d’attribut avant la `Authentication` paramètre n’est pas _aucun_, la valeur par défaut est `Yes`. Sinon, la valeur par défaut est `No`. La valeur de l’attribut avant de chiffrement est `Yes` si la valeur est définie sur `Yes` dans la chaîne de la source de données ou de la connexion.|

## <a name="new-andor-modified-connection-attributes"></a>Attributs de connexion nouvelles / modifiées

Les éléments suivants de préconnexion connexion attributs ont été introduites ou modifiés pour prendre en charge l’authentification Azure Active Directory. Lorsqu’un attribut de connexion a une chaîne de connexion correspondante ou le mot clé DSN et est défini, l’attribut de connexion est prioritaire.

|Attribut|Type|Valeurs|Valeur par défaut| Description|
|-|-|-|-|-|
|`SQL_COPT_SS_AUTHENTICATION`|`SQL_IS_INTEGER`|`SQL_AU_NONE`, `SQL_AU_PASSWORD`, `SQL_AU_AD_INTEGRATED`, `SQL_AU_AD_PASSWORD`, `SQL_AU_RESET`|(non défini)|Consultez la description de `Authentication` mot clé ci-dessus. `SQL_AU_NONE`est fourni afin de substituer explicitement un ensemble `Authentication` valeur dans la chaîne de connexion et/ou de la source de données, tandis que `SQL_AU_RESET` unsets l’attribut si elle a été définie, ce qui permet de la valeur de chaîne de connexion ou de la source de données sont prioritaires.|
|`SQL_COPT_SS_ACCESS_TOKEN`|`SQL_IS_POINTER`|Pointeur vers `ACCESSTOKEN` ou NULL|NULL|_Seuls les pilotes Windows_. Si non null, spécifie le jeton d’accès organisation à utiliser. Il s’agit d’une erreur pour spécifier un jeton d’accès et également `UID`, `PWD`, `Trusted_Connection`, ou `Authentication` mots clés de chaîne de connexion ou de leurs attributs équivalents.|
|`SQL_COPT_SS_ENCRYPT`|`SQL_IS_INTEGER`|`SQL_EN_OFF`, `SQL_EN_ON`|(voir description)|Contrôle le chiffrement pour une connexion. `SQL_EN_OFF`et `SQL_EN_ON` désactiver et activer le chiffrement, respectivement. Si la valeur d’attribut avant la `Authentication` paramètre n’est pas _aucun_ ou `SQL_COPT_SS_ACCESS_TOKEN` est défini, et `Encrypt` n’était pas spécifiée dans la chaîne de la source de données ou de la connexion, la valeur par défaut est `SQL_EN_ON`. Sinon, la valeur par défaut est `SQL_EN_OFF`. La valeur effective de cet attribut contrôle [utilisation de chiffrement pour la connexion.](https://docs.microsoft.com/en-us/sql/relational-databases/native-client/features/using-encryption-without-validation)|
|`SQL_COPT_SS_OLDPWD`|\-|\-|\-|Non pris en charge avec Azure Active Directory, étant donné que les modifications de mot de passe pour les entités de sécurité AAD ne peut pas être effectuées via une connexion ODBC. <br><br>Expiration du mot de passe pour l’authentification SQL Server a été introduite dans SQL Server 2005. Le `SQL_COPT_SS_OLDPWD` attribut a été ajouté pour permettre au client fournir l’ancien et le nouveau mot de passe pour la connexion. Lorsque cette propriété est définie, le fournisseur n'utilisera pas le pool de connexions pour la première connexion ou pour les connexions suivantes, puisque la chaîne de connexion contiendra l'« ancien mot de passe » qui a maintenant changé.|
|`SQL_COPT_SS_INTEGRATED_SECURITY`|`SQL_IS_INTEGER`|`SQL_IS_OFF`,`SQL_IS_ON`|`SQL_IS_OFF`|_Déconseillé_; utilisez `SQL_COPT_SS_AUTHENTICATION` la valeur `SQL_AU_AD_INTEGRATED` à la place. <br><br>Force l’utilisation de l’authentification Windows (Kerberos sur Linux et macOS) pour la validation de l’accès sur la connexion au serveur. Lorsque l’authentification Windows est utilisée, le pilote ignore les valeurs d’identificateur et le mot de passe utilisateur fournis dans le cadre de `SQLConnect`, `SQLDriverConnect`, ou `SQLBrowseConnect` de traitement.|

## <a name="ui-additions-for-azure-active-directory-windows-driver-only"></a>Compléments d’interface utilisateur pour Azure Active Directory (pilote Windows uniquement)

Le programme d’installation de la source de données et les interfaces utilisateur de connexion du pilote ont été améliorés avec les options supplémentaires nécessaires à l’utilisation de l’authentification auprès d’Azure AD.

### <a name="creating-and-editing-dsns-in-the-ui"></a>Création et modification de sources de données dans l’interface utilisateur

Il est possible d’utiliser la nouveau répertoire Azure AD les options d’authentification lors de la création ou modification d’une source de données existante à l’aide de l’interface utilisateur d’installation du pilote :

`Authentication=ActiveDirectoryIntegrated`pour l’authentification intégrée à Active Directory de Azure vers SQL Azure

![CreateNewDSN3.png](windows/CreateNewDSN3.png)

`Authentication=ActiveDirectoryPassword`pour l’authentification du nom d’utilisateur/mot de passe Azure Active Directory pour SQL Azure

![CreateNewDSN4.png](windows/CreateNewDSN4.png)

`Authentication=SqlPassword`pour l’authentification du nom d’utilisateur/mot de passe à SQL Server (Azure ou autre)

![CreateNewDSN.png](windows/CreateNewDSN.png)

`Trusted_Connection=Yes`pour Windows SSPI hérité une authentification intégrée

![CreateNewDSN2.png](windows/CreateNewDSN2.png)

Les quatre options correspondent aux `Trusted_Connection=Yes` (Windows hérité existant SSPI uniquement l’authentification intégrée) et `Authentication=` `ActiveDirectoryIntegrated`, `SqlPassword`, et `ActiveDirectoryPassword`, respectivement.

### <a name="sqldriverconnect-prompt-windows-driver-only"></a>SQLDriverConnect invite (pilote Windows uniquement)

La boîte de dialogue invite de commandes affichée par SQLDriverConnect lorsqu’il demande des informations nécessaires pour effectuer la connexion contient deux nouvelles options pour l’authentification Azure AD :

![SQLServerLogin.png](windows/SQLServerLogin.png)

Ces options correspondent aux quatre mêmes disponibles dans le programme d’installation DSN UI ci-dessus.

### <a name="example-connection-strings"></a>Exemples de chaîne de connexion
1. Authentification SQL Server – syntaxe héritée. Certificat de serveur n’est pas validé, et le chiffrement est utilisé uniquement si le serveur applique. Le nom d’utilisateur/mot de passe est passé dans la chaîne de connexion.
`server=Server;database=Database;UID=UserName;PWD=Password;`
2. Authentification SQL – nouvelle syntaxe. Le client demande le chiffrement (la valeur par défaut `Encrypt` est `true`) et le certificat de serveur obtient validé, quel que soit le paramètre de chiffrement (à moins que `TrustServerCertificate` a la valeur `true`). Le nom d’utilisateur/mot de passe est passé dans la chaîne de connexion.
 `server=Server;database=Database;UID=UserName;PWD=Password;Authentication=SqlPassword;`
3. L’authentification intégrée Windows (Kerberos sur Linux et macOS) à l’aide de SSPI (pour SQL Server ou SQL IaaS) – syntaxe actuelle. Certificat de serveur n’est pas validé, sauf si le chiffrement est utilisé. 
`server=Server;database=Database;Trusted_Connection=yes;`
4. (_Pilote Windows uniquement_.) L’authentification intégrée Windows à l’aide de SSPI (si la base de données cible est dans SQL Server ou SQL IaaS) – nouvelle syntaxe. Le client demande le chiffrement (la valeur par défaut `Encrypt` est `true`) et le certificat de serveur obtient validé, quel que soit le paramètre de chiffrement (à moins que `TrustServerCertificate` a la valeur `true`). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
5. Nom d’utilisateur/mot de passe l’authentification AAD (si la base de données cible est dans la base de données SQL Azure). Certificat de serveur est validé, quel que soit le paramètre de chiffrement (à moins que `TrustServerCertificate` a la valeur `true`). Le nom d’utilisateur/mot de passe est passé dans la chaîne de connexion. 
`server=Server;database=Database;UID=UserName;PWD=Password;Authentication=ActiveDirectoryPassword;`
6. (_Pilote Windows uniquement_.) Authentification Windows intégrée à l’aide de la bibliothèque ADAL, ce qui implique l’échange des informations d’identification du compte Windows pour un jeton d’accès d’AAD émis, en supposant que la base de données cible est dans la base de données SQL Azure. Certificat de serveur est validé, quel que soit le paramètre de chiffrement (à moins que `TrustServerCertificate` a la valeur `true`). 
`server=Server;database=Database; Authentication=ActiveDirectoryIntegrated;`

> [!NOTE] 
>- Lorsque vous utilisez les nouvelles options d’Active Directory avec le pilote ODBC de Windows, assurez-vous que le [bibliothèque d’authentification Active Directory pour SQL Server](http://go.microsoft.com/fwlink/?LinkID=513072) a été installé. Les pilotes Linux et macOS ne nécessitent pas toutes les dépendances supplémentaires pour l’authentification avec Azure Active Directory.
>- Pour vous connecter à l’aide d’un nom d’utilisateur du compte SQL Server et le mot de passe, vous pouvez maintenant utiliser le nouveau `SqlPassword` option, ce qui est recommandée en particulier pour SQL Azure, car cette option active les paramètres par défaut de connexion plus sécurisées.
>- Pour vous connecter à l’aide d’un nom d’utilisateur du compte Azure Active Directory et le mot de passe, spécifiez `Authentication=ActiveDirectoryPassword` dans la chaîne de connexion et le `UID` et `PWD` mots clés avec le nom d’utilisateur et un mot de passe, respectivement.
>- Pour vous connecter à l’aide intégrée de Windows ou authentification intégrée à Active Directory (pilote Windows uniquement), spécifiez `Authentication=ActiveDirectoryIntegrated` dans la chaîne de connexion. Le pilote choisit automatiquement le mode d’authentification approprié. `UID`et `PWD` ne doit pas être spécifié.

## <a name="authenticating-with-an-access-token-windows-driver-only"></a>L’authentification avec un jeton d’accès (pilote Windows uniquement)

Le `SQL_COPT_SS_ACCESS_TOKEN` attribut de préconnexion autorise l’utilisation d’un jeton d’accès obtenu d’Azure AD pour l’authentification au lieu de nom d’utilisateur et mot de passe et ignore également la négociation et l’obtention d’un jeton d’accès par le pilote. Pour utiliser un jeton d’accès, définissez la `SQL_COPT_SS_ACCESS_TOKEN` attribut de connexion à un pointeur vers un `ACCESSTOKEN` structure :

~~~
typedef struct AccessToken
{
    DWORD dataSize;
    BYTE data[];
} ACCESSTOKEN;
~~~

Le `ACCESSTOKEN` est une structure de longueur variable constituée de 4 octets _longueur_ suivie _longueur_ octets de données opaques qui forment le jeton d’accès. En raison de la manière dont SQL Server gère les jetons d’accès, une obtenus via une [OAuth 2.0](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-authentication-scenarios) réponse JSON doit être étendu afin que chaque octet est suivi d’un octet, similaire à une chaîne de UCS-2 contenant uniquement des caractères ASCII de remplissage de 0 ; Toutefois, le jeton est une valeur opaque et la longueur spécifiée, en octets, ne doivent pas inclure toute marque de fin null. En raison de leurs contraintes de longueur et le format considérables, cette méthode d’authentification est uniquement disponible par programmation via la `SQL_COPT_SS_ACCESS_TOKEN` coonnection attribut ; aucune source de données correspondante ou le mot clé de chaîne de connexion. La chaîne de connexion ne doit pas contenir `UID`, `PWD`, `Authentication`, ou `Trusted_Connection` mots clés.

## <a name="azure-active-directory-authentication-sample-code"></a>Exemple de Code Azure Active Directory d’authentification

L’exemple suivant montre le code requis pour se connecter à SQL Server à l’aide d’Azure Active Directory avec les mots clés de connexion. Notez qu’il n’est pas nécessaire de modifier le code d’application lui-même ; la chaîne de connexion ou DSN si elle est utilisée, est la seule modification nécessaire à l’authentification AAD :
~~~
    ...
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server};UID=myuser;PWD=myPass;Authentication=ActiveDirectoryPassword"
    ...
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    ...
~~~
L’exemple suivant montre le code requis pour se connecter à SQL Server à l’aide d’Azure Active Directory avec l’authentification de jeton d’accès. Dans ce cas, il est nécessaire de modifier le code d’application pour traiter le jeton d’accès et de définir l’attribut de connexion associée.
~~~
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server}"
    SQLCHAR accessToken[] = "eyJ0eXAiOi..."; // In the format extracted from an OAuth JSON response
    ...
    DWORD dataSize = 2 * strlen(accessToken);
    ACCESSTOKEN *pAccToken = malloc(sizeof(ACCESSTOKEN) + dataSize);
    pAccToken->dataSize = dataSize;
    // Expand access token with padding bytes
    for(int i = 0, j = 0; i < dataSize; i += 2, j++) {
        pAccToken->data[i] = accessToken[j];
        pAccToken->data[i+1] = 0;
    }
    ...
    SQLSetConnectAttr(hDbc, SQL_COPT_SS_ACCESS_TOKEN, (SQLPOINTER)pAccToken, SQL_IS_POINTER);
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);      
    ...
    free(pAccToken);
~~~

## <a name="see-also"></a>Voir aussi
[Prise en charge de l’authentification basée sur le jeton de base de données SQL Azure à l’aide d’Azure AD Authentication](https://blogs.msdn.microsoft.com/sqlsecurity/2016/02/09/token-based-authentication-support-for-azure-sql-db-using-azure-ad-auth)


