**You**: Clang plugin boilerplate




```cpp
#include "clang/Frontend/FrontendPluginRegistry.h"
#include "clang/AST/AST.h"
#include "clang/AST/ASTConsumer.h"
#include "clang/AST/RecursiveASTVisitor.h"
#include "clang/Frontend/CompilerInstance.h"
#include "clang/Sema/Sema.h"
#include <iostream>

using namespace clang;

class MyASTVisitor : public RecursiveASTVisitor<MyASTVisitor> {
public:
  explicit MyASTVisitor(ASTContext *Context) : Context(Context) {}

  bool VisitFunctionDecl(FunctionDecl *FD) {
    std::cout << "Function: " << FD->getNameInfo().getName().getAsString() << std::endl;
    return true;
  }

private:
  ASTContext *Context;
};

class MyASTConsumer : public ASTConsumer {
public:
  explicit MyASTConsumer(ASTContext *Context)
      : Visitor(Context) {}

  virtual void HandleTranslationUnit(ASTContext &Context) {
    Visitor.TraverseDecl(Context.getTranslationUnitDecl());
  }

private:
  MyASTVisitor Visitor;
};

class MyFrontendAction : public ASTFrontendAction {
public:
  virtual std::unique_ptr<ASTConsumer> CreateASTConsumer(CompilerInstance &CI,
                                                         StringRef file) {
    return llvm::make_unique<MyASTConsumer>(&CI.getASTContext());
  }
};

static FrontendPluginRegistry::Add<MyFrontendAction>
X("my-plugin", "my plugin description");
```
