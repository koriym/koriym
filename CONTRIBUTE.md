---
title: Guide to Open Source Contributions
description: A comprehensive guide for beginners on how to contribute to open source projects
author: Akihito Koriyama
date: 2025-02-07
categories:
  - Open Source
tags:
  - GitHub
  - Testing
  - PHPUnit
  - Contribution Guidelines  
---

# 👋 Path to Open Source Contributions

> 💡 **Please report anything you notice, no matter how small:**
> The problems you experience are likely being experienced by others too.
> Your report could be the first step towards improving the project.

## 🌱 First Step: Become an Issue Reporter!

> 💡 **Value your insights about "someone else might be struggling with this too"!**
>
> Everyone feels nervous about their first issue report:
> - "Is this report valuable..."
> - "Maybe others aren't having this problem..."
> - "Does it have to be in English..."
>
> But your insights are valuable information:
> - Someone else is probably struggling with the same problem
> - With a report, there's a chance for fixing it ⭐️
> - Reports in other languages are welcome too 🤗

### Basic Issue Structure

```markdown
## Overview
[Concise explanation of the problem]

## Steps to Reproduce
1. [Specific step 1]
2. [Specific step 2]
3. [Specific step 3]

## Expected Behavior
[How it should work]

## Actual Behavior
[How it currently works]

## Environment Information (if needed)
- OS: [OS name and version]
- Command version: x.x.x
```

> 🤖 **If you're struggling with writing an issue:**
> Try sharing the error message and situation with AI and ask "Please write this in issue format."
> The AI will help organize the problem description. Review it and you're ready to post!

## 🌿 Next Step: Become a Test Writer!

> 💡 **Tests are the best problem reports!**
>
> Tests help everyone: 🤝
> - Can verify issues without setting up reproduction environment 👍
> - Quick verification of fixes 👍
> - Clear expected behavior 👍
> - Automatic problem detection going forward 👍

### PHPUnit Basics

> Remember the AAA (Arrange-Act-Assert) pattern and writing tests becomes simple:
>
> 1. **Arrange**: Set up the stage
> 2. **Act**: Perform the main action
> 3. **Assert**: Verify the outcome
>
> These 3 steps express code behavior like a story!

```php
use PHPUnit\Framework\TestCase;

class StringCalculatorTest extends TestCase
{
    public function testCanAddNumbers()
    {
        // 1. Create test instance (Arrange)
        $calc = new StringCalculator();

        // 2. Execute test target (Act)
        $result = $calc->add("1,2");

        // 3. Verify results (Assert)
        $this->assertEquals(3, $result);
    }

    public function testEmptyStringReturnsZero()
    {
        $calc = new StringCalculator();
        $result = $calc->add("");
        $this->assertEquals(0, $result);
    }

    public function testCanHandleNewLines()
    {
        $calc = new StringCalculator();
        $result = $calc->add("1\n2,3");
        $this->assertEquals(6, $result);
    }

    /**
     * @dataProvider additionProvider
     */
    public function testBasicAdditionCases($input, $expected)
    {
        $calc = new StringCalculator();
        $result = $calc->add($input);
        $this->assertEquals($expected, $result);
    }

    public function additionProvider()
    {
        return [
            'single number' => ['1', 1],
            'two numbers' => ['1,2', 3],
            'three numbers' => ['1,2,3', 6],
            'calculation with zero' => ['0,1,2', 3],
        ];
    }
}
```

## 🌳 Further Growth: Become a Problem Solver!

> 💡 **Turn that "I wish I could fix this" feeling into action!**
>
> Everyone feels uncertain about bug fixes and feature improvements at first:
> - "The codebase is so large..."
> - "I'm worried about the impact of changes..."
> - "Is this approach correct..."
>
> But don't worry. AI and [MergeClip](https://github.com/koriym/MergeClip) will support your problem-solving journey!

### Step 1: Understanding the Problem

```bash
# Import related code with MergeClip
mergeclip /path/to/related/files
# Or select related files in Finder, right-click > Quick Actions > MergeClip
# Example questions for AI about code and problems
"Please explain how the code related to this issue works"
"What could be causing this bug?"
```

### Step 2: Considering Solutions
```bash
# Example AI consultations
"Please suggest ways to fix this bug"
"What could be the impact of this change on other parts?"
```

### Step 3: Implementing Fixes
```bash
# Verify fix proposals with AI
"Is this fix approach appropriate?"
"Please suggest necessary test cases"
```

## Summary

1. **Start with Small Steps**
    - Begin by reporting what you notice
    - Utilize AI support

2. **Contribute to Quality with Tests**
    - Start with concrete examples
    - Comprehensive testing with data providers

3. **Take on Problem Solving**
    - Utilize AI and MergeClip
    - Approach gradually

Your contributions directly improve project quality!
Let's grow together with the project 🌟

## 🎯 Fork & Pull Request Guide

Here's the standard GitHub contribution process. Even beginners can follow with confidence!

```bash
# 1. Fork repository (Click "Fork" button on GitHub)
# 2. Clone fork locally
git clone https://github.com/your-username/repository-name.git

# 3. Create working branch (good practice: don't work directly on main)
git checkout -b feature/your-changes

# 4. Make and commit changes
# (after editing files)
git add .
git commit -m "Brief description of changes"

# 5. Push to fork
git push origin feature/your-changes

# 6. Create pull request on GitHub
# → Click "Compare & pull request" that appears automatically after push
# → Create PR targeting original repository
```

**💡 Common Pitfalls**

- Cloning without forking → Push permission errors
- Making changes directly on main → More likely to have conflicts later
- Wrong pull request target → Always select "original repository"

**🖼️ Visual Guide (GitHub UI)**

1. Click "Fork" on original repository
2. Select your account to create fork
3. Copy clone URL from "Code" button on forked repository
4. Click "Open pull request" banner that appears after push
5. Verify "base repository" is original and "head repository" is your fork
6. Review changes and click "Create pull request"

**🚀 Advanced Techniques**

```bash
# Add original repository as upstream (to stay up-to-date)
git remote add upstream https://github.com/original-owner/repository-name.git

# Get latest main branch
git fetch upstream
git checkout main
git merge upstream/main
```

⚠️ Note that "main" might be **master** or **1.x** in some cases

**❓ "Not sure where to target the pull request?"**
- Always create targeting the **original repository's main branch**
- Select in GitHub's PR creation screen:
  ```
  base repository: original-owner/repository-name (main branch)
  head repository: your-username/repository-name (feature branch)
  ```

This submits your changes to the project!  
It might be confusing the first time, but it gets smoother from the second time ✨  
Don't hesitate to ask project maintainers if you have any questions!

https://koriym.github.io/koriym/CONTRIBUTE
