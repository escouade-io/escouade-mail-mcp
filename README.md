# escouade-mail-mcp

*Français : [README.fr.md](README.fr.md)*

**Escouade Mail** (formerly Subagent) gives your AI agent a real mailbox: it writes, receives and replies with its own address. It is one hosted MCP server:

```text
https://api.subagent.fr/mcp
```

Connect it in any client that accepts a remote MCP server (Streamable HTTP). This repository holds no tool code: it shows how to connect, client by client, and publishes the server's contract.

## In two steps

**1. Without a key.** Connect the address alone. The server then shows a single tool, `sign_up`. Ask your agent: "Sign up to Escouade Mail, my e-mail is marie@example.com." It receives a key, shown once, and a mailbox on `subagentmail.fr`. You receive a 6-digit code by e-mail.

**2. With the key.** Store the key in an environment variable, then connect again with the `Authorization` header. Your agent now sees the tools its key opens. Give it the code: it calls `verify`, and sending opens.

```sh
claude mcp add --transport http escouade-mail https://api.subagent.fr/mcp \
  --header "Authorization: Bearer $SUBAGENT_KEY"
```

The configuration of each client (Claude Code, Claude Desktop, Cursor, VS Code, Codex and others) is in the French guide and in `configs/`.

## Documentation

- Guides and the reference of every tool: https://escouade.io/mail/docs (in French)
- The server's contract: `mcp-manifest.json` in this repository

## Contributing

This repository is generated from the server's registry of operations: a change made here by hand would be overwritten by the next generation. Please open an issue rather than a pull request.

## License

MIT. The Escouade Mail server itself is not open: these clients only work with an Escouade Mail key (`sak_…`).
