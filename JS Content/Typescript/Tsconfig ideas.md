#### Basic config
```JSON
{
  "compilerOptions": {
    "target": "es2016",
    "module": "Node16",
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "strict": true,
    "skipLibCheck": true,
    "moduleResolution": "Node16"
  },
  "exclude": [
    "node_modules/"
  ],
  "include": [
    "src/**/*", // TS should check and compile all files inside src dir
  ],
  "exclude": ["node_modules", "build", "**/*.spec.ts"], // Don't do typechecking in these files
}
```

