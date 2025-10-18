# API Reference

Complete API documentation for the Octarine MCP Server. This document provides detailed specifications for all available tools, including parameters, return types, error codes, and usage examples.

## Table of Contents

- [Overview](#overview)
- [Data Types](#data-types)
- [Error Handling](#error-handling)
- [Tools](#tools)
- [Best Practices](#best-practices)
- [Rate Limiting](#rate-limiting)
- [Examples](#examples)

## Overview

The Octarine MCP Server exposes four primary tools for interacting with markdown notes in workspaces. All tools follow consistent patterns for parameters, return values, and error handling.

### Base Concepts

- **Workspace**: An isolated collection of notes with its own directory structure
- **Note Path**: Relative path to a note file within a workspace
- **Content**: UTF-8 encoded markdown text with optional frontmatter

### Communication Protocol

All communication uses the MCP (Model Context Protocol) standard over stdio.

For complete detailed API documentation with all TypeScript interfaces, error codes, and extensive examples, see the full version at: https://github.com/m0rfiin-m/octarine-mcp-server/blob/main/docs/API_REFERENCE.md

## Quick Reference

### octarine_read_note
Read note contents from workspace.

### octarine_write_note
Create or update notes in workspace.

### octarine_search_notes
Search notes by content across workspaces.

### octarine_list_notes
List all notes in a workspace or directory.

---

*This is an abbreviated version. Full API documentation with complete TypeScript definitions, error handling patterns, and comprehensive examples is available in the GitHub repository.*
