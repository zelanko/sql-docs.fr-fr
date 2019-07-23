---
title: Utilisation de Azure Active Directory avec le pilote ODBC | Microsoft Docs pour SQL Server
ms.custom: ''
ms.date: 11/08/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 52205f03-ff29-4254-bfa8-07cced155c86
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9e60c376e0bced63241674b82d05700281a06ad3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008490"
---
# <a name="using-azure-active-directory-with-the-odbc-driver"></a>Utilisation d’Azure Active Directory avec ODBC Driver
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="purpose"></a>Fonction

La Microsoft ODBC Driver for SQL Server avec la version 13,1 ou ultérieure permet aux applications ODBC de se connecter à une instance de SQL Azure à l’aide d’une identité fédérée dans Azure Active Directory avec un nom d’utilisateur/mot de passe, un jeton d’accès Azure Active Directory, un jeton d’accès Azure active Identité du service administré de l’annuaire ou authentification intégrée Windows (_pilote Windows uniquement_). Pour la version 13,1 du pilote ODBC, l’authentification par jeton d’accès Azure Active Directory est _Windows uniquement_. Le pilote ODBC version 17 et ultérieures prennent en charge cette authentification sur toutes les plateformes (Windows, Linux et Mac). Une nouvelle Azure Active Directory l’authentification interactive avec l’ID de connexion est introduite dans la version 17,1 du pilote ODBC pour Windows. Une nouvelle Azure Active Directory méthode d’authentification d’identité de service managée a été ajoutée dans la version du pilote ODBC 17.3.1.1 pour les identités affectées par le système et affectées par l’utilisateur. Toutes ces connexions sont accomplies à l’aide de nouveaux mots clés de chaîne de connexion et de DSN, ainsi que des attributs de connexion.

> [!NOTE]
> Le pilote ODBC sur Linux et macOS ne prend pas en charge Services ADFS. Si vous utilisez Azure Active Directory l’authentification par nom d’utilisateur/mot de passe à partir d’un client Linux ou macOS et que votre configuration de Active Directory comprend des services fédérés, l’authentification peut échouer.

## <a name="new-andor-modified-dsn-and-connection-string-keywords"></a>Mots clés de chaîne de connexion et de DSN nouveaux et/ou modifiés

Le `Authentication` mot clé peut être utilisé lors de la connexion à un DSN ou une chaîne de connexion pour contrôler le mode d’authentification. La valeur définie dans la chaîne de connexion remplace celle figurant dans le DSN, si elle est fournie. La _valeur pré-attribut_ du `Authentication` paramètre est la valeur calculée à partir de la chaîne de connexion et des valeurs DSN.

|Créer une vue d’abonnement|Valeurs|Valeur par défaut|Description|
|-|-|-|-|
|`Authentication`|(non défini), (chaîne vide), `SqlPassword` `ActiveDirectoryIntegrated`, `ActiveDirectoryPassword` `ActiveDirectoryInteractive`,,,`ActiveDirectoryMsi` |(non défini)|Contrôle le mode d’authentification.<table><tr><th>Valeur<th>Description<tr><td>(non défini)<td>Mode d’authentification déterminé par d’autres mots clés (options de connexion héritées existantes).<tr><td>(chaîne vide)<td>La chaîne de connexion est « {0} » Remplacez et annulez une `Authentication` valeur définie dans le DSN.<tr><td>`SqlPassword`<td>S’authentifier directement auprès d’une instance de SQL Server en utilisant un nom d’utilisateur et un mot de passe.<tr><td>`ActiveDirectoryPassword`<td>S’authentifier avec une identité Azure Active Directory à l’aide d’un nom d’utilisateur et d’un mot de passe.<tr><td>`ActiveDirectoryIntegrated`<td>_Pilote Windows uniquement_. S’authentifier avec une identité Azure Active Directory à l’aide de l’authentification intégrée.<tr><td>`ActiveDirectoryInteractive`<td>_Pilote Windows uniquement_. S’authentifier avec une identité Azure Active Directory à l’aide de l’authentification interactive.<tr><td>`ActiveDirectoryMsi`<td>S’authentifier avec Azure Active Directory identité à l’aide de l’authentification Managed Service Identity. Pour l’identité attribuée par l’utilisateur, UID est défini sur l’ID d’objet de l’identité d’utilisateur.</table>|
|`Encrypt`|(non défini), `Yes`, `No`|(voir la description)|Contrôle le chiffrement pour une connexion. Si la valeur de pré-attribut du `Authentication` paramètre n’est pas _None_ dans le DSN ou la chaîne de connexion, `Yes`la valeur par défaut est. Sinon, la valeur par défaut est `No`. Si l’attribut `SQL_COPT_SS_AUTHENTICATION` remplace la valeur de pré-Attribute de `Authentication`, définissez explicitement la valeur du chiffrement dans le DSN ou la chaîne de connexion ou l’attribut de connexion. La valeur pré-attribute du chiffrement est `Yes` si la valeur est définie sur `Yes` dans le DSN ou la chaîne de connexion.|

## <a name="new-andor-modified-connection-attributes"></a>Attributs de connexion nouveaux et/ou modifiés

Les attributs de connexion pré-connexion suivants ont été introduits ou modifiés pour prendre en charge l’authentification Azure Active Directory. Lorsqu’un attribut de connexion a une chaîne de connexion ou un mot clé DSN correspondant et qu’il est défini, l’attribut de connexion est prioritaire.

|Attribute|Type|Valeurs|Valeur par défaut|Description|
|-|-|-|-|-|
|`SQL_COPT_SS_AUTHENTICATION`|`SQL_IS_INTEGER`|`SQL_AU_NONE`, `SQL_AU_PASSWORD`, `SQL_AU_AD_INTEGRATED`, `SQL_AU_AD_PASSWORD`, `SQL_AU_AD_INTERACTIVE`, `SQL_AU_AD_MSI`, `SQL_AU_RESET`|(non défini)|Consultez la description `Authentication` du mot clé ci-dessus. `SQL_AU_NONE`est fourni pour remplacer explicitement une valeur Set `Authentication` dans le DSN et/ou la chaîne de connexion, tout en `SQL_AU_RESET` annulant la définition de l’attribut si celui-ci a été défini, ce qui permet à la valeur de la chaîne de connexion ou du DSN d’être prioritaire.|
|`SQL_COPT_SS_ACCESS_TOKEN`|`SQL_IS_POINTER`|`ACCESSTOKEN` Pointeur ou null|NULL|Si la valeur est non null, spécifie le jeton d’accès AzureAD à utiliser. La spécification d’un jeton `UID`d’accès et également `PWD` `Trusted_Connection`,, ou `Authentication` de mots clés de chaîne de connexion ou leurs attributs équivalents constitue une erreur. <br> **Remarque:** La version 13,1 du pilote ODBC ne prend en charge que cette version sur _Windows_.|
|`SQL_COPT_SS_ENCRYPT`|`SQL_IS_INTEGER`|`SQL_EN_OFF`, `SQL_EN_ON`|(voir la description)|Contrôle le chiffrement pour une connexion. `SQL_EN_OFF`et `SQL_EN_ON` désactivez et activez le chiffrement, respectivement. Si la valeur de pré-attribut du `Authentication` paramètre n’est pas _None_ `SQL_COPT_SS_ACCESS_TOKEN` ou est définie et `Encrypt` qu’elle n’a pas été spécifiée dans la chaîne de connexion ou le `SQL_EN_ON`DSN, la valeur par défaut est. Sinon, la valeur par défaut est `SQL_EN_OFF`. Si l’attribut `SQL_COPT_SS_AUTHENTICATION` de connexion est défini sur not _None_, affectez `SQL_COPT_SS_ENCRYPT` explicitement la valeur souhaitée si `Encrypt` n’est pas spécifié dans le DSN ou la chaîne de connexion. La valeur effective de cet attribut contrôle [si le chiffrement sera utilisé pour la connexion.](https://docs.microsoft.com/sql/relational-databases/native-client/features/using-encryption-without-validation)|
|`SQL_COPT_SS_OLDPWD`|\-|\-|\-|Non pris en charge avec Azure Active Directory, car les modifications de mot de passe des principaux AAD ne peuvent pas être effectuées par le biais d’une connexion ODBC. <br><br>L’expiration du mot de passe pour l’authentification SQL Server a été introduite dans SQL Server 2005. L' `SQL_COPT_SS_OLDPWD` attribut a été ajouté pour permettre au client de fournir l’ancien et le nouveau mot de passe pour la connexion. Lorsque cette propriété est définie, le fournisseur n'utilisera pas le pool de connexions pour la première connexion ou pour les connexions suivantes, puisque la chaîne de connexion contiendra l'« ancien mot de passe » qui a maintenant changé.|
|`SQL_COPT_SS_INTEGRATED_SECURITY`|`SQL_IS_INTEGER`|`SQL_IS_OFF`,`SQL_IS_ON`|`SQL_IS_OFF`|_Déconseillé_; Utilisez `SQL_COPT_SS_AUTHENTICATION` à`SQL_AU_AD_INTEGRATED` la place. <br><br>Force l’utilisation de l’authentification Windows (Kerberos sur Linux et macOS) pour la validation de l’accès sur la connexion au serveur. Lorsque l’authentification Windows est utilisée, le pilote ignore les valeurs d’identificateur d’utilisateur et de mot `SQLConnect`de `SQLDriverConnect`passe fournies `SQLBrowseConnect` dans le cadre du traitement, ou.|

## <a name="ui-additions-for-azure-active-directory-windows-driver-only"></a>Ajouts de l’interface utilisateur pour Azure Active Directory (pilote Windows uniquement)

La configuration du DSN et les interfaces utilisateur de connexion du pilote ont été améliorées avec les options supplémentaires nécessaires à l’utilisation de l’authentification avec Azure AD.

### <a name="creating-and-editing-dsns-in-the-ui"></a>Création et modification des noms de sources de l’interface utilisateur

Il est possible d’utiliser les nouvelles options d’authentification Azure AD lors de la création ou de la modification d’un DSN existant à l’aide de l’interface utilisateur du programme d’installation du pilote:

`Authentication=ActiveDirectoryIntegrated` pour l’authentification intégrée Azure Active Directory à SQL Azure

![CreateNewDSN_ADIntegrated.png](windows/CreateNewDSN_ADIntegrated.png)

`Authentication=ActiveDirectoryPassword`pour Azure Active Directory l’authentification par nom d’utilisateur/mot de passe à SQL Azure

![CreateNewDSN_ADPassword.png](windows/CreateNewDSN_ADPassword.png)

`Authentication=ActiveDirectoryInteractive` pour l’authentification interactive Azure Active Directory à SQL Azure

![CreateNewDSN_ADInteractive.png](windows/CreateNewDSN_ADInteractive.png)

`Authentication=SqlPassword`pour l’authentification par nom d’utilisateur/mot de passe pour SQL Server (Azure ou autre)

![CreateNewDSN_SQLServer.png](windows/CreateNewDSN_SQLServer.png)

`Trusted_Connection=Yes`pour l’authentification intégrée SSPI héritée de Windows

![CreateNewDSN_winSSPI.png](windows/CreateNewDSN_winSSPI.png)

Les cinq options correspondent à `Trusted_Connection=Yes` (authentification intégrée de Windows SSPI uniquement existante) `SqlPassword`et `ActiveDirectoryPassword` `Authentication=` `ActiveDirectoryIntegrated`,, et `ActiveDirectoryInteractive`, respectivement.

### <a name="sqldriverconnect-prompt-windows-driver-only"></a>Invite SQLDriverConnect (pilote Windows uniquement)

La boîte de dialogue d’invite affichée par SQLDriverConnect lorsqu’elle demande des informations requises pour terminer la connexion contient trois nouvelles options pour l’authentification Azure AD:

![ServerLogin.png](windows/ServerLogin.png)

Ces options correspondent aux cinq mêmes cinq disponibles dans l’interface utilisateur de configuration de DSN ci-dessus.

### <a name="example-connection-strings"></a>Exemples de chaîne de connexion
1. Authentification SQL Server-syntaxe héritée. Le certificat de serveur n’est pas validé et le chiffrement est utilisé uniquement si le serveur l’applique. Le nom d’utilisateur/mot de passe est transmis dans la chaîne de connexion.
`server=Server;database=Database;UID=UserName;PWD=Password;`
2. Authentification SQL-nouvelle syntaxe. Le client demande le chiffrement (la valeur `Encrypt` par `true`défaut est) et le certificat du serveur est validé, quel que soit le `TrustServerCertificate` paramètre de chiffrement `true`(sauf si a la valeur). Le nom d’utilisateur/mot de passe est transmis dans la chaîne de connexion.
 `server=Server;database=Database;UID=UserName;PWD=Password;Authentication=SqlPassword;`
3. Authentification Windows intégrée (Kerberos sur Linux et macOS) à l’aide de SSPI (vers SQL Server ou SQL IaaS)-syntaxe actuelle. Le certificat de serveur n’est pas validé, sauf si le chiffrement est utilisé. 
`server=Server;database=Database;Trusted_Connection=yes;`
4. (_Pilote Windows uniquement_.) Authentification Windows intégrée à l’aide de SSPI (si la base de données cible est en SQL Server ou SQL IaaS)-nouvelle syntaxe. Le client demande le chiffrement (la valeur `Encrypt` par `true`défaut est) et le certificat du serveur est validé, quel que soit le `TrustServerCertificate` paramètre de chiffrement `true`(sauf si a la valeur). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
5. Authentification par nom d’utilisateur/mot de passe AAD (si la base de données cible est dans Azure SQL DB). Le certificat de serveur est validé, quel que soit le paramètre `TrustServerCertificate` de chiffrement `true`(sauf si a la valeur). Le nom d’utilisateur/mot de passe est transmis dans la chaîne de connexion. 
`server=Server;database=Database;UID=UserName;PWD=Password;Authentication=ActiveDirectoryPassword;`
6. (_Pilote Windows uniquement_.) Authentification Windows intégrée à l’aide de ADAL, qui implique l’échange d’informations d’identification de compte Windows pour un jeton d’accès émis par AAD, en supposant que la base de données cible se trouve dans Azure SQL Database. Le certificat de serveur est validé, quel que soit le paramètre `TrustServerCertificate` de chiffrement `true`(sauf si a la valeur). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
7. (_Pilote Windows uniquement_.) L’authentification interactive AAD utilise la technologie Azure Multi-Factor Authentication pour configurer la connexion. Dans ce mode, en fournissant l’ID de connexion, une boîte de dialogue d’authentification Windows Azure est déclenchée et permet à l’utilisateur d’entrer le mot de passe pour terminer la connexion. Le nom d’utilisateur est transmis dans la chaîne de connexion.
`server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

![WindowsAzureAuth.png](windows/WindowsAzureAuth.png)

8. L’authentification Managed Service Identity AAD utilise l’identité attribuée par le système ou l’identité affectée par l’utilisateur pour l’authentification pour configurer la connexion. Pour l’identité attribuée par l’utilisateur, UID est défini sur l’ID d’objet de l’identité d’utilisateur.<br>
Pour l'identité affectée par le système,<br>
`server=Server;database=Database;Authentication=ActiveDirectoryMsi;`<br>
Pour une identité affectée par l’utilisateur avec un ID d’objet égal à myObjectId,<br>
`server=Server;database=Database;UID=myObjectId;Authentication=ActiveDirectoryMsi;`

> [!NOTE] 
>- Lorsque vous utilisez les nouvelles options de Active Directory avec le pilote ODBC de Windows, assurez-vous que le [bibliothèque d’Authentification Active Directory pour SQL Server](https://go.microsoft.com/fwlink/?LinkID=513072) a été installé. Lorsque vous utilisez les pilotes Linux et MacOS, vérifiez `libcurl` que a été installé. Pour le pilote version 17,2 et versions ultérieures, il ne s’agit pas d’une dépendance explicite, car elle n’est pas requise pour les autres méthodes d’authentification ou les opérations ODBC.
>- Pour vous connecter à l’aide d’un nom d’utilisateur et d’un mot de `SqlPassword` passe de compte SQL Server, vous pouvez maintenant utiliser la nouvelle option, qui est recommandée pour les SQL Azure, car cette option active des paramètres de connexion plus sécurisés.
>- Pour vous connecter en utilisant un nom d’utilisateur et un `Authentication=ActiveDirectoryPassword` mot de passe de compte Azure Active Directory `UID` , `PWD` spécifiez dans la chaîne de connexion et les mots clés et avec le nom d’utilisateur et le mot de passe, respectivement.
>- Pour vous connecter à l’aide de l’authentification Windows intégrée ou Active Directory intégrée (pilote `Authentication=ActiveDirectoryIntegrated` Windows uniquement), spécifiez dans la chaîne de connexion. Le pilote choisira automatiquement le mode d’authentification approprié. `UID`et `PWD` ne doivent pas être spécifiés.
>- Pour vous connecter à l’aide de l’authentification Active Directory interactive ( `UID` pilote Windows uniquement), vous devez spécifier.

## <a name="authenticating-with-an-access-token"></a>Authentification avec un jeton d’accès

L' `SQL_COPT_SS_ACCESS_TOKEN` attribut de préconnexion autorise l’utilisation d’un jeton d’accès obtenu à partir d’Azure AD pour l’authentification au lieu du nom d’utilisateur et du mot de passe, et contourne également la négociation et l’obtention d’un jeton d’accès par le pilote. Pour utiliser un jeton d’accès, définissez `SQL_COPT_SS_ACCESS_TOKEN` l’attribut de connexion sur un pointeur `ACCESSTOKEN` désignant une structure:

~~~
typedef struct AccessToken
{
    DWORD dataSize;
    BYTE data[];
} ACCESSTOKEN;
~~~

Est une structure de longueur variable composée d’une _longueur_ de 4 octets suivie d’octets de _longueur_ des données opaques qui forment le jeton d’accès.`ACCESSTOKEN` En raison de la façon dont SQL Server gère les jetons d’accès, l’un obtenu via une réponse JSON [2,0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios) JSON doit être développé afin que chaque octet soit suivi d’un octet de remplissage 0, similaire à une chaîne UCS-2 contenant uniquement des caractères ASCII. Toutefois, le jeton est une valeur opaque et la longueur spécifiée, en octets, ne doit inclure aucune marque de fin null. En raison de leurs contraintes de format et de longueur considérables, cette méthode d’authentification n’est disponible par `SQL_COPT_SS_ACCESS_TOKEN` programmation qu’à l’aide de l’attribut de connexion; il n’existe aucun DSN ou mot clé de chaîne de connexion correspondant. La chaîne de connexion ne doit `UID`pas `PWD`contenir de mots `Trusted_Connection` clés,, `Authentication`ou.

> [!NOTE]
> La version 13,1 du pilote ODBC ne prend en charge que cette authentification sur _Windows_.

## <a name="azure-active-directory-authentication-sample-code"></a>Exemple de code d’authentification Azure Active Directory

L’exemple suivant montre le code requis pour se connecter à SQL Server à l’aide de Azure Active Directory avec des mots clés de connexion. Notez qu’il n’est pas nécessaire de modifier le code d’application lui-même; la chaîne de connexion, ou DSN si elle est utilisée, est la seule modification nécessaire pour utiliser AAD pour l’authentification:
~~~
    ...
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server};UID=myuser;PWD=myPass;Authentication=ActiveDirectoryPassword"
    ...
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    ...
~~~
L’exemple suivant montre le code requis pour se connecter à SQL Server à l’aide de Azure Active Directory avec l’authentification de jeton d’accès. Dans ce cas, il est nécessaire de modifier le code de l’application pour traiter le jeton d’accès et définir l’attribut de connexion associé.
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
Voici un exemple de chaîne de connexion à utiliser avec l’authentification interactive Azure Active Directory. Notez qu’il ne contient pas le champ PWD, car le mot de passe est entré à l’aide de l’écran d’authentification Windows Azure.
~~~
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myuser;Authentication=ActiveDirectoryInteractive"
~~~
Voici un exemple de chaîne de connexion à utiliser avec l’authentification Azure Active Directory Managed Service Identity. Notez que l’UID est défini sur l’ID d’objet de l’identité attribuée par d’utilisateur.
~~~
// For system-assigned identity,
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};Authentication=ActiveDirectoryMsi"
...
// For user-assigned identity with object ID equals to myObjectId
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myObjectId;Authentication=ActiveDirectoryMsi"
~~~

## <a name="see-also"></a>Voir aussi
[Prise en charge de l’authentification basée sur les jetons pour Azure SQL DB à l’aide de l’authentification Azure AD](https://blogs.msdn.microsoft.com/sqlsecurity/2016/02/09/token-based-authentication-support-for-azure-sql-db-using-azure-ad-auth)

