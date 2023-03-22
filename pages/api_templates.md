# API Templates 

---

Jargon uses templates to customise how OpenAPI Specifications are generated from your Domains 

## How to create an API Template

### Individuals and Teams

1. Browse to the profile page of the account you want to create a template in
2. Click the 'Open Settings' button above the profile picture
3. Click the 'OpenAPI' menu item, underneath the 'Tempplates' headding
4. Click the 'New template' button
5. Enter a name for the new template, and fill in the template's content
6. Click the 'Save Templates' button

### Enterprise 

1. Navigate to the Management Console
2. Click the 'OpenAPI Templates' menu item
3. Click the 'New template' button
4. Enter a name for the new template, and fill in the template's content
5. Click the 'Save Templates' button


## The format of an API Template

### Minimum Viable Template

Here is an example of a minimal template:

```json
{
  "meta": {
    "description": "An Empty template"
  },
  "content": {
    "openapi": "3.0.0",
    "info": {
      "title": "",
      "description": "",
      "version": "1"
    },
    "paths": {}
  }
}
```

There are two root objects, **meta** and **content**

### meta

This holds the descriptive and configuration objects for the template

Only a **description** is required, as per the above minimal example.

A more typical example looks like this:

```json
"meta": {
    "description": "A Sample meta object",
    "defaults": {
        "responses": [
            "400",
            "401",
            "403",
            "404",
            "500"
        ],
		"params": [
			"token"
		],
        "security": {
            "get": {
                "OAuth2": [
                    "read"
                ],
                "OpenID": [
                    "read"
                ]
            },
            "put,patch,post,delete": {
                "OAuth2": [
                    "write"
                ],
                "OpenID": [
                    "write"
                ]
            }
        }
    },
    "configuration": {
        "oidc_scopes_supported": {
            "OpenID": [
                "read",
                "write"
            ]
        }
    }
}
```


#### description

A brief description of this API Template, shown when selecting templates.

### defaults

Applies the following settings to all paths in the API, which then can be individually customised in the API Editor.

#### responses

An array of responses to apply to all paths. Each arry entry must have a corresponding definition in **#/content/components/responses**

#### params 

An array of parameters to apply to all paths. Each arry entry must have a corresponding definition in **#/content/components/parameters**

#### security 

An object with key values of the comma-separated http verbs that the security will apply to.
Each comma-separated http verb object is an object with keys that must correspond to a definition in **#/content/components/security** and contain an array of scope names within that security definition.

**Note for OIDC** OIDC scopes are defined outside of the OpenAPI specification. To use OIDC security schemes, you will need to add the apporpirate oidc configuration, described below.

#### configuration

An object that holds configuration data

#### oidc_scopes_supported

OIDC scopes are defined outside the OpenAPI specification. Jargon needs additional inforamtion to populate the API Editor with the allowable OIDC scopes.

Each key within this object must correspond to a security definition in **#/content/components/security** that has a **type** of **openIdConnect**


### content

This object holds the content of a standard OpenAPI specification or Swagger file.

Jargon will insert the required paths and schemas / components into this object.

Jargon supports a small set of customisations withinn the OpenAPI spcification object

#### Generated Security Scopes

Jargon can generate security scopes based on the Domain model, driven by the **[oas.securityScopeAcronym]** attribute. See the page on [key-value pairs](pages/data_definitions?id=jargon-recognised-key-value-pairs) for details.

You will need to insert a security definition in **#/content/components/security**. Insetead of specifying the scopes manually, add **"autogen:true** as the only child of the scopes object. 


```json
 "AuthorizerScheme": {
	"description": "JWT access token",
	"type": "oauth2",
	"flows": {
		"authorizationCode": {
			"authorizationUrl": "/authorize",
			"tokenUrl": "/oauth20/token",
			"refreshUrl": "/oauth20/token",
			"scopes": {
				"autogen": true
			}
		}
	}
}
```


## Sample Template

```json
{
	"meta": {
		"description": "Sample template",
		"configuration": {
			"oidc_scopes_supported": {
				"OpenID": [
					"read",
					"write"
				]
			}
		},
		"defaults": {
			"responses": [
				"400",
				"401",
				"403",
				"404",
				"500"
			],
			"params": [
				"token"
			],
			"security": {
				"get": {
					"OAuth2": [
						"read"
					],
					"OpenID": [
						"read"
					]
				},
				"put,patch,post,delete": {
					"OAuth2": [
						"write"
					],
					"OpenID": [
						"write"
					]
				}
			}
		}
	},
	"content": {
		"openapi": "3.0.0",
		"info": {
			"description": "# Introduction\nThis template is intended to to be a good starting point for describing\nhow users can interact with the various methods of your API. \nWe recommend informing the user about various aspects of your api such as:\n\n\n# Getting Started\n\n## Using The API\n\n## Extra Developer Documentation:\nIf you have more developer documentation or tutorials specific to helping\ndevelopers interact with this endpoint.\n**url:** 'https://example.com/documentation/link'\n\n# Uptime & Planned Outages\n\n# Authentication & Rate Limits\n# Terms of Use, Copyright and Attribution\nPlease ensure you comply with the following policies prior to using any data\nwithin this API.\n\n- [Terms of Use](https://example.com/terms-use)\n- [Privacy Policy](https://example.com/privacy)\n\n# Contact Us\n",
			"contact": {
				"email": "youremail@example.com",
				"url": "https://example.com/contact"
			},
			"version": "unpublished",
			"title": "Example.com"
		},
		"paths": {},
		"components": {
			"schemas": {
				"Template_ErrorSchema": {
					"type": "object",
					"properties": {
						"errors": {
							"type": "array",
							"items": {
								"$ref": "#/components/schemas/Template_Error"
							},
							"description": ""
						}
					}
				},
				"Template_Error": {
					"type": "object",
					"properties": {
						"id": {
							"type": "string",
							"readOnly": true,
							"description": ""
						},
						"detail": {
							"type": "string",
							"description": ""
						},
						"code": {
							"type": "string",
							"description": ""
						},
						"source": {
							"$ref": "#/components/schemas/Template_ErrorSource"
						}
					}
				},
				"Template_ErrorSource": {
					"type": "object",
					"properties": {
						"pointer": {
							"type": "string",
							"description": ""
						},
						"parameter": {
							"type": "string",
							"description": ""
						}
					}
				}
			},
			"parameters": {
				"token": {
					"name": "token",
					"in": "header",
					"description": "token to be passed as a header",
					"required": true,
					"schema": {
						"type": "array",
						"items": {
							"type": "integer",
							"format": "int64"
						}
					},
					"style": "simple"
				}
			},
			"responses": {
				"201": {
					"description": "Created."
				},
				"202": {
					"description": "Accepted."
				},
				"204": {
					"description": "No content."
				},
				"400": {
					"description": "Bad Request.",
					"content": {
						"application/json": {
							"schema": {
								"$ref": "#/components/schemas/Template_ErrorSchema"
							},
							"examples": {
								"response": {
									"value": "{\n  \"errors\": [\n    {\n      \"id\": \"86032cbe-a804-4c3b-86ce-ec3041e3effc\",\n      \"detail\": \"Invalid value(s) in request input\",\n      \"code\": \"19283\",\n      \"source\": {\n        \"parameter\": \"postcode\"\n      }\n    },\n    {\n      \"id\": \"45786a8f-452e-492f-a779-801b5d0bd0a7\",\n      \"detail\": \"Input value(s) exceeded maximum length\",\n      \"code\": \"19284\",\n      \"source\": {\n        \"parameter\": \"last_name\"\n      }\n    }\n  ]\n}\n"
								}
							}
						}
					}
				},
				"401": {
					"description": "Unauthorised.",
					"content": {
						"application/json": {
							"examples": {
								"response": {
									"value": "{\n  \"status\": \"401\",\n  \"description\": \"The request could not be authenticated.\",\n  \"more_info\": \"\"\n}\n"
								}
							}
						}
					}
				},
				"403": {
					"description": "Forbidden.",
					"content": {
						"application/json": {
							"examples": {
								"response": {
									"value": "{\n  \"status\": \"403\",\n  \"description\": \"The request was authenticated but is not authorised to access the resource.\",\n  \"more_info\": \"\"\n}\n"
								}
							}
						}
					}
				},
				"404": {
					"description": "Not found.",
					"content": {
						"application/json": {
							"examples": {
								"response": {
									"value": "{\n  \"status\": \"404\",\n  \"description\": \"The resource was not found.\",\n  \"more_info\": \"\"\n}\n"
								}
							}
						}
					}
				},
				"405": {
					"description": "Not Allowed.",
					"content": {
						"application/json": {
							"examples": {
								"response": {
									"value": "{\n  \"status\": \"405\",\n  \"description\": \"The method is not implemented for this resource. The response may include an Allow header containing a list of valid methods for the resource.\",\n  \"more_info\": \"\"\n}\n \n"
								}
							}
						}
					}
				},
				"408": {
					"description": "Request Timeout.",
					"content": {
						"application/json": {
							"examples": {
								"response": {
									"value": "{\n  \"status\": \"408\",\n  \"description\": \"The request timed out before a response was received.\",\n  \"more_info\": \"\"\n}\n"
								}
							}
						}
					}
				},
				"415": {
					"description": "Unsupported Media Type.",
					"content": {
						"application/json": {
							"examples": {
								"response": {
									"value": "{\n  \"status\": \"415\",\n  \"description\": \"This status code indicates that the server refuses to accept the request because the content type specified in the request is not supported by the server.\",\n  \"more_info\": \"\"\n}\n"
								}
							}
						}
					}
				},
				"422": {
					"description": "Unprocessable Entity.",
					"content": {
						"application/json": {
							"examples": {
								"response": {
									"value": "{\n  \"status\": \"422\",\n  \"description\": \"This status code indicates that the server received the request but it did not fulfil the requirements of the back end. An example is a mandatory field was not provided in the payload.\",\n  \"more_info\": \"\"\n}\n"
								}
							}
						}
					}
				},
				"500": {
					"description": "Internal Server Error.",
					"content": {
						"application/json": {
							"examples": {
								"response": {
									"value": "{\n  \"status\": \"500\",\n  \"description\": \"An internal server error. The response body may contain error messages.\",\n  \"more_info\": \"\"\n}\n \n"
								}
							}
						}
					}
				},
				"501": {
					"description": "Method Not Implemented.",
					"content": {
						"application/json": {
							"examples": {
								"response": {
									"value": "{\n  \"status\": \"501\",\n  \"description\": \"It indicates that the request method is not supported by the server and cannot be handled for any resource For example, the server supports GET, POST, PUT, DELETE, and PATCH but not OPTIONS methods.\",\n  \"more_info\": \"\"\n}"
								}
							}
						}
					}
				},
				"503": {
					"description": "Service Unavailable.",
					"content": {
						"application/json": {
							"examples": {
								"response": {
									"value": "{\n  \"status\": \"503\",\n  \"description\": \"The server is not ready to handle the request. A Retry-After HTTP header, if present, will contain the estimated time for recovery and retry.\",\n  \"more_info\": \"\"\n}"
								}
							}
						}
					}
				}
			},
			"securitySchemes": {
				"OpenID": {
					"type": "openIdConnect",
					"openIdConnectUrl": "https://example.com/.well-known/openid-configuration"
				},
				"OAuth2": {
					"type": "oauth2",
					"flows": {
						"authorizationCode": {
							"authorizationUrl": "https://example.com/oauth2/authorize",
							"tokenUrl": "https://example.com/oauth2/token",
							"scopes": {
								"read": "Grants read access",
								"write": "Grants write access"
							}
						}
					}
				}
			}
		}
	}
}
```
